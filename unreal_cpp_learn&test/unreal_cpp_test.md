# 第一章 C++编程入门

## 1.2.3 使属性出现在编辑器中

类创建完成后可使用特殊宏UNROPERTY()将属性公开到编辑器  

```cpp
UCLASS()
class AmyActor:public AActor{
    GENERATED_BODY()

    UNROPERTY(EDitAnywhere)
    int32 TotalDamage;
}
```

即可在编辑器中对数值进行编辑。可像宏中传入跟多信息完成此操作。
![测试用]()
