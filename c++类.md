## C++中的类
### 类支持面向对象编程思想
***
>**举个例子**
***
设想在一个游戏中，玩家会以某种方式代表。要怎样去表示一个玩家？  
需要一些表示玩家的数据，如玩家在游戏里的位置；其他属性：移动速度，还有模型来显示在屏幕上。  
所有数据都需要存在某个地方，还可以为这些数据创建变量
```cpp
int main(){
    int Playerx,Playery;
    int Playerspeed=2;

    std::cin.get();
}
```
这是创建一个玩家需要的数据变量，如果游戏中需要两个玩家，那么，这些数据变量将一次一次重复写入
```cpp
int main(){
    int Player0x,Player0y;
    int Player0speed=2;

    int Player1x,Player1y;
    int Player1speed=2;
    std::cin.get();
}
```

为了不一次次在代码里写入无组织的变量，显然不能这么写  
同时还有一个原因  
如果像编写一个函数用来移动角色
```cpp
int Move(int x,int y,int speed){

}
```
这样会产生很多代码，变得无法维护  
可以用类来简化这一步  
* 创建一个Player类   
```cpp
class Player//类型的定义
{
	int Playerx, Playery;
	int Playerspeed;
};

int main()
{
	Player player;//由类型制成的变量叫做对象，新创建对象的过程
	std::cin.get();
}
```
以上代码创建一个类型为Player的player的对象  
```cpp
Player player;
```
这行代码作用为实例化一个Player对象  
要设置这些变量
```cpp
Player player;
player.Playerx = 1;
```
此时编译后，编译器会报错
***  
* 访问控制
***
默认情况下类中成员的访问控制都是私有的，只有类内部的函数才能访问这些变量  
如果要从main函数中访问这些变量需将类中代码改为
```cpp
class Player
{
public:
	int Playerx, Playery;
	int Playerspeed;
};
```
将类的访问控制改为共有  
共有表示可以在类以外任何地方去访问这些变量  
***
>做点别的事
***
假设在你在拥有了所有数据，现在想移动  
编写一个函数来改变X，Y变量
```cpp
void Move(Player& player,int xa,int ya)
{
	player.Playerx += xa * player.Playerspeed;
	player.Playery += ya * player.Playerspeed;
}
```
调用此函数  
```cpp
int main()
{
	Player player;
	Move(player,1, -1);
	std::cin.get();
}
```
更好的做法  
类里面可以包含函数，可以将Move函数写进类里  
**类内函数称作方法**  

>将Move函数写进类里



```cpp
class Player
{
public:
	int Playerx, Playery;
	int Playerspeed;

	void Move(int xa, int ya)
	{
		Playerx += xa * Playerspeed;
		Playery += ya * Playerspeed;
	}
};

void Move(Player& player,int xa,int ya)
{
	player.Playerx += xa * player.Playerspeed;
	player.Playery += ya * player.Playerspeed;
}

int main()
{
	Player player;
	Move(player,1, -1);
	player.Move(1, 1);
	std::cin.get();
}
```
现在访问变量不需要传递player对象，已经在player类内了  
main函数只需要player.move()  

### 总结
**类就是使我们能对变量进行组织，变成一个类型，还为这些变量添加了函数