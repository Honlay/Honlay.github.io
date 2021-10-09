---
layout: post
title: Unity摄影机旋转
date: 2021-01-01 20:20:23 +0900
category: Unity
---

### PC端摄影机旋转脚本

```c#
using UnityEngine;
using UnityEngine.EventSystems;
/// <summary>
/// 摄影机旋转
/// </summary>
public class CameraOrbit : MonoSingleton<CameraOrbit>
{
    //目标点
    public Transform target;
    //x轴旋转速度
    public float speedX = 200f;
    //y轴旋转速度
    public float speedY = 200f;
    //滚轮缩放速度
    public float speed = 5f;
    //y轴限制最小角度
    public float minY = 0f;
    //y轴限制最大角度
    public float maxY = 90f;
    
    //摄影机与目标点距离
    public float distance = 100f;
    //最小距离
    public float minDistance = 0f;
    //最大距离
    public float maxDistance = 200f;

    //是否开启阻尼
    public bool isDamping = true;
    //阻尼值
    private float damping = 5.0f;
    //x轴旋转角度
    public float x = 0.0f;
    //y轴旋转角度
    public float y = 0.0f;
    //中心
    private Vector3 _center;
    private Vector3 _prevPos = Vector3.zero;
    
    //初始数据
    private float _originalX;
    private float _originalY;
    private float _originalDistance;
    private Vector3 _originalTargetPosition;
    private Vector3 _originalCameraPosition;
    private Quaternion _originalCameraRotation;
    private float _originalSpeed;
    //拖拽
    public bool isDragEnabled=true;
    //目标点移动速度
    public float moveSpeed =10f;
    //目标点最小高度
    public float minHeight = -10f;
    //目标点最大高度
    public float maxHeight = 40f;
    

    private void OnEnable()
    {
        _center = GetComponent<Camera>().ScreenToWorldPoint(new Vector3(Screen.width / 2, Screen.height / 2, 0));
    }

    private void Start()
    {
        var angles = transform.eulerAngles;
        x = angles.y;
        y = angles.x;

        GetOriginalData();
    }

    private void Update()
    {
        //滚轮速度控制
        SpeedControl();
        //Distance微调
        DistanceControl();
        //摄影机旋转
        CameraRotation();
        //摄影机拖拽
        CameraDrag();
        //目标点移动
        TargetMoved();
    }

    #region Private Function
    private static float ClampAngle(float angle, float min, float max)
    {
        if (angle < -360)
            angle += 360;
        if (angle > 360)
            angle -= 360;
        return Mathf.Clamp(angle, min, max);
    }
    /// <summary>
    /// 滚轮速度控制
    /// </summary>
    private void SpeedControl()
    {
        if (distance >= 30f)
            speed = distance / 3f;
        else
            speed = 10f;

        if (Input.GetKey(KeyCode.LeftShift))
            speed = _originalSpeed;
    }
    /// <summary>
    /// 获取摄影机初始数据
    /// </summary>
    private void GetOriginalData()
    {
        var t =this.transform;
        _originalCameraPosition = t.position;
        _originalCameraRotation = t.rotation;
        _originalTargetPosition = target.position;
        _originalX = x;
        _originalY = y;
        _originalDistance = distance;
        _originalSpeed = speed;
    }
    /// <summary>
    /// 摄影机旋转
    /// </summary>
    private void CameraRotation()
    {
        if (Input.GetMouseButton(1))
        {
            x += Input.GetAxis("Mouse X") * speedX * 0.02f;
            y -= Input.GetAxis("Mouse Y") * speedY * 0.02f;
            y = ClampAngle(y, minY, maxY);
        }

        if (!EventSystem.current.IsPointerOverGameObject())
        {
            distance -= Input.GetAxis("Mouse ScrollWheel") * speed;
        }
        
        if (target)
            distance = Mathf.Clamp(distance, minDistance, maxDistance);
        
        var rotation = Quaternion.Euler(y, x, 0.0f);
        Vector3 disVector;
        Vector3 position;
        
        if (target)
        {
            disVector = new Vector3(0.0f, 0.0f, -distance);
            position = rotation * disVector + target.position;
        }
        else
        {
            disVector = new Vector3(0.0f, 0.0f, -Vector3.Distance(transform.position, _center));
            position = rotation * disVector + _center;
        }
        
        if (isDamping)
        {
            Transform transform1;
            (transform1 = transform).rotation = Quaternion.Lerp(transform.rotation, rotation, Time.deltaTime * damping);
            transform.position = Vector3.Lerp(transform1.position, position, Time.deltaTime * damping);
        }
        else
        {
            var transform1 = transform;
                                                       transform1.rotation = rotation;
                                                       transform1.position = position;
        }
    }
    /// <summary>
    /// 摄影机拖拽
    /// </summary>
    private void CameraDrag()
    {
        if (!isDragEnabled) return;
        if (Input.GetMouseButtonDown(2))
        {
            var screenSpace = GetComponent<Camera>().WorldToScreenPoint(target.position);
            _prevPos = new Vector3(Input.mousePosition.x, Input.mousePosition.y, screenSpace.z);
        }

        if (Input.GetMouseButtonUp(2))
        {
            _prevPos = Vector3.zero;
        }

        if (!Input.GetMouseButton(2)) return;
        {
            if (EventSystem.current.IsPointerOverGameObject()) return;
            var position = target.position;
            var screenSpace = GetComponent<Camera>().WorldToScreenPoint(position);

            var currPos = new Vector3(Input.mousePosition.x, Input.mousePosition.y, screenSpace.z);

            var prev = GetComponent<Camera>().ScreenToWorldPoint(_prevPos);
            var curr = GetComponent<Camera>().ScreenToWorldPoint(currPos);

            var offset = curr - prev;

            offset.y = 0;

            position += -offset;
            target.position = position;

            _prevPos = currPos;
        }
    }
    /// <summary>
    /// 目标点拖拽
    /// </summary>
    private void TargetMoved()
    {
        if(EventSystem.current.IsPointerOverGameObject())
            return;
        if(Input.GetKey(KeyCode.UpArrow))
            target.transform.Translate(0, Time.deltaTime * moveSpeed, 0);
        else if (Input.GetKey(KeyCode.DownArrow))
            target.transform.Translate(0, Time.deltaTime * moveSpeed*-1, 0);

        var pos = target.transform.position;
        if (pos.y <= minHeight)
            target.transform.position = new Vector3(pos.x, minHeight, pos.z);
        if (pos.y >= maxHeight)
            target.transform.position = new Vector3(pos.x, maxHeight, pos.z);
    }
    /// <summary>
    /// 摄影机与目标点距离微雕快捷键
    /// </summary>
    private void DistanceControl()
    {
        if (Input.GetKeyDown(KeyCode.RightBracket)) //]
            distance++;
        else if (Input.GetKeyDown(KeyCode.LeftBracket)) //[
            distance--;
    }
    #endregion

    #region Public Function
    /// <summary>
    /// 重置摄影机位置
    /// </summary>
    public void ResetCamera()
    {
        var transform1 = this.transform;
        transform1.position = _originalCameraPosition;
        transform1.rotation = _originalCameraRotation;
        target.position = _originalTargetPosition;

        x = _originalX;
        y = _originalY;

        distance = _originalDistance;
    }
    /// <summary>
    /// 设置摄影机视角
    /// </summary>
    /// <param name="targetPos">目标点位置</param>
    /// <param name="dis">距离</param>
    public void SetCameraView(Vector3 targetPos, float dis)
    {
        target.transform.position = targetPos;
        distance = dis;
    }

    #endregion
    
}

```

