---
layout: post
title: C#单例模式二
date: 2021-10-08 20:20:23 +0900
category: Unity
---

## 切换场景时销毁

```c#
using UnityEngine;
/// <summary>
/// 单例模式
/// </summary>
/// <typeparam name="T"></typeparam>
public abstract class MonoSingleton<T> : MonoBehaviour where T : MonoSingleton<T>{
	
	private static T m_Instance = null;

    //设计阶段 脚本没有挂在物体上
    //运行时 需要这个脚本的唯一实例，调用instance
    public static T Instance
    {
        get
        {
			if( m_Instance == null )
            {
            	m_Instance = GameObject.FindObjectOfType(typeof(T)) as T;
                if( m_Instance == null )
                {
                    m_Instance = new GameObject(typeof(T).ToString(), typeof(T)).GetComponent<T>();
					m_Instance.Init();
                }
               
            }
            return m_Instance;
        }
    }

    //设计阶段 脚本挂载物体上
    private void Awake()
    {
   
        if( m_Instance == null )
        {
            m_Instance = this as T;
        }
    }
 
    public virtual void Init(){}
 

    private void OnApplicationQuit()
    {
        m_Instance = null;
    }
}
```

