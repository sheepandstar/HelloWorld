### 创建Dog类
``` python
class Dog():
    """一次模拟小狗的简单尝试"""

    def __init__(self, name, age):
        """初始化属性name和age"""
        self.name = name
        self.age = age

    def sit(self):
        """模拟小狗被命令时蹲下"""
        print(self.name.title() + " is now sitting.")

    def roll_over(self):
        """模拟小狗被命令时打滚"""
        print(self.name.title() + " rolled over!")

my_dog = Dog('willie',6)

print("My dog's name is " + my_dog.name.title() + ".")
print("My dog is " + str(my_dog.age) + " years old.")

my_dog.sit()
my_dog.roll_over()

your_dog = Dog('lucy',3)
your_dog.roll_over()
```

### 输出结果：   
My dog's name is Willie.   
My dog is 6 years old.   
Willie is now sitting.   
Willie rolled over!   
Lucy rolled over!  



### 注意：
1. __init__()是一个特殊的方法，每当我们根据Dog类创建新实例时，python都会自动运行它。在这个方法中，开头和末尾各有两个下划线。其中，形参self必不可少，还必须位于其他形参的前面。        
2. 每个与类相关联的方法调用都自动传递实参self（因此我们不需要传递它），它是一个指向实例本身的引用，让实例能够访问类中的属性和方法。     
3. 根据约定，在python中，手写字母大写的名称是指类。而小写名称指的是根据类创建的实例。   
