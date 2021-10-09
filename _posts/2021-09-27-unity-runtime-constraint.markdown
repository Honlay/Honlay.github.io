---
layout: post
title: Unity运行时添加/删除Constraint组件
date: 2021-09-27 19:20:23 +0900
category: Unity
---

Unity2018中新增了约束组件。
我们知道如何使用它，但在脚本中如何操作，请查看以下内容
## 关于Unity对象的父子关系
在常规的Unity父子关系中，父子关系是一对多的，并且子对象的Tansform是首父对象影响的。
但是，UI 的缺点是子对象总是位于最前面。 看来原因是如果你有父子关系，你不能划分图层，如果是UI，即使你更改图层设置也不会应用它。
当然，您可以通过在 Sprite Renderer 的 Sorting Layer 中设置渲染顺序来解决此问题。 然而，这带来了无法使用 UI 的可悲结果。
## 关于约束
约束组件允许您使用对象与其它对象的关系进行行为设置限制。
**注意**
为方便起见，在以下的解释中，将影响其它对象的对象称为”父对象“。
主观上来说，Constraint具有三个特点：
- 父子关系可以形成多对一的形式
- 由于UI不需要创建父子关系，只要改变其在Hierarchy的位置就可以改变UI的渲染顺序
- 受Constraints约束的形式有3种：Positon only、Rotation only、Parents，可以根据情况使用。

## 步骤
1.获取Constraint系统组件
2.创建ConstraintSource结构，设置限制哪个对象
3.将2中创建的ConstraintSource添加到Constraint
## 关键点
1.添加父对象的元素时，必须创建ConstarintSource，并在其中添加对象的Transform信息。
2.ConstarintSource的Impact Weight 还需要设置为 1。
## 脚本
```c#
using UnityEngine;
//使用约束时需引入命名空间
using UnityEngine.Animations;

public class ConstraintTest : MonoBehaviour
{
    private ConstraintSource myConstraintSource;
    private PositionConstraint myPositionConstraint;

    public Transform parent;

    private void Start()
    {
        myPositionConstraint = GetComponent<PositionConstraint>();
        SetObject2ConstraintSource(parent);
    }

    private void SetObject2ConstraintSource(Transform parent)
    {
        this.myConstraintSource.sourceTransform = parent;
        this.myConstraintSource.weight = 1.0f;

        this.myPositionConstraint.AddSource(this.myConstraintSource); 
        this.myPositionConstraint.translationOffset = Vector3.zero;  
        this.myPositionConstraint.enabled = true;
    }

    private void DeleteSource()
    {
        this.myPositionConstraint.RemoveSource(0);
        this.myPositionConstraint.enabled = false;

    }
}

```

