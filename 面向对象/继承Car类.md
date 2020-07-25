### 继承
``` python
class Car():
    """一次模拟汽车的简单尝试"""

    def __init__(self ,make, model, year):
        self.make = make
        self.model = model
        self.year = year
        self.odometer_reading = 0

    def get_descriptive_name(self):
        long_name = str(self.year) + ' ' + self.make + ' ' + self.model 
        return long_name.title()

    def read_odometer(self):
        print('This car has ' + str(self.odometer_reading) + ' miles on it.')

    def update_odometer(self,mileage):
        if mileage >= self.odometer_reading:
            self.odometer_reading = mileage
        else:
            print("You can't roll back an odometer!")

    def increment_odometer(self,miles):
        self.odometer_reading += miles
    

class ElectricCar(Car):
    """电动汽车的独特之处"""

    def __init__(self,make,model,year):
        """初始化父类的属性"""
        super().__init__(make,model,year)
my_tesla = ElectricCar('tesla','model s ',2016)
print(my_tesla.get_descriptive_name())
```


### 输出结果：    
2016 Tesla Model S   

### 小结：   
1. 创建子类实例时，Python首先需要完成的任务时给父类的所有属性赋值，为此子类的方法__init__()需要父类施以援手。
2. 创建子类时，父类必须包含在当前文件中，且位于子类前面。
3. 定义子类时，必须在括号内指定父类的名称。
4. super()是一个特殊函数，帮助Python将父类和子类关联起来。

### 给子类定义属性和方法：
``` python 
class Car():
    """一次模拟汽车的简单尝试"""

    def __init__(self ,make, model, year):
        self.make = make
        self.model = model
        self.year = year
        self.odometer_reading = 0

    def get_descriptive_name(self):
        long_name = str(self.year) + ' ' + self.make + ' ' + self.model 
        return long_name.title()

    def read_odometer(self):
        print('This car has ' + str(self.odometer_reading) + ' miles on it.')

    def update_odometer(self,mileage):
        if mileage >= self.odometer_reading:
            self.odometer_reading = mileage
        else:
            print("You can't roll back an odometer!")

    def increment_odometer(self,miles):
        self.odometer_reading += miles
    

class ElectricCar(Car):

    def __init__(self,make,model,year):
        """
        电动汽车的独特之处
        初始化父类的属性，再初始化电动汽车特有的属性
        """
        super().__init__(make,model,year)
        self.battery_size = 70

    def describe_battery(self):
        """打印一条描述电瓶容量的消息"""
        print("This car has a " + str(self.battery_size) + '-kwh battery.')


my_tesla = ElectricCar('tesla','model s ',2016)
print(my_tesla.get_descriptive_name())
my_tesla.describe_battery()

```

##### 输出结果:   
2016 Tesla Model S      
This car has a 70-kwh battery.   


### 重写父类的方法：
对于父类的方法，只要它不符合子类模拟的实物的行为，都可对其进行重写。为此，可在子类中定义一个这样的方法，即它与要重写的父类方法同名。这样，python将不好考虑这个父类方法，而只关注你在子类中定义相应的方法。
如，在子类电动车中重写父类方法wheel_num（）


``` python
class Car():
    """一次模拟汽车的简单尝试"""

    def __init__(self ,make, model, year):
        self.make = make
        self.model = model
        self.year = year
        self.odometer_reading = 0

    def get_descriptive_name(self):
        long_name = str(self.year) + ' ' + self.make + ' ' + self.model 
        return long_name.title()

    def read_odometer(self):
        print('This car has ' + str(self.odometer_reading) + ' miles on it.')

    def update_odometer(self,mileage):
        if mileage >= self.odometer_reading:
            self.odometer_reading = mileage
        else:
            print("You can't roll back an odometer!")

    def increment_odometer(self,miles):
        self.odometer_reading += miles

    def wheel_num(self):
        """打印汽车轮子数量"""
        print("A car has 4 wheels")
    

class ElectricCar(Car):

    def __init__(self,make,model,year):
        """
        电动汽车的独特之处
        初始化父类的属性，再初始化电动汽车特有的属性
        """
        super().__init__(make,model,year)
        self.battery_size = 70

    def describe_battery(self):
        """打印一条描述电瓶容量的消息"""
        print("This car has a " + str(self.battery_size) + '-kwh battery.')

    def wheel_num(self):
        """打印电动车轮子数量"""
        print("A electeiccar has 2 wheels or 4 wheels")


my_tesla = ElectricCar('tesla','model s ',2016)
print(my_tesla.get_descriptive_name())
my_tesla.describe_battery()
my_tesla.wheel_num()
```


##### 输出结果：   
2016 Tesla Model S      
This car has a 70-kwh battery.    
A electeiccar has 2 wheels or 4 wheels   

### 将实例用作属性

``` python
class Car():
    """一次模拟汽车的简单尝试"""

    def __init__(self ,make, model, year):
        self.make = make
        self.model = model
        self.year = year
        self.odometer_reading = 0

    def get_descriptive_name(self):
        long_name = str(self.year) + ' ' + self.make + ' ' + self.model 
        return long_name.title()

    def read_odometer(self):
        print('This car has ' + str(self.odometer_reading) + ' miles on it.')

    def update_odometer(self,mileage):
        if mileage >= self.odometer_reading:
            self.odometer_reading = mileage
        else:
            print("You can't roll back an odometer!")

    def increment_odometer(self,miles):
        self.odometer_reading += miles

    
class Battery():
    """一次模拟电动汽车电瓶的简单尝试"""

    def __init__(self,battery_size=70):
        """初始化电瓶的属性"""
        self.battery_size = battery_size

    def describe_battery(self):
        """打印一条描述电瓶容量的消息"""
        print("This car has a " + str(self.battery_size) + "-kwh battery.")


class ElectricCar(Car):
    """电动汽车的独特之处"""
    def __init__(self,make,model,year,battery):
        """
        初始化父类的属性，再初始化电动汽车特有的属性
        """
        super().__init__(make,model,year)
        self.battery = Battery(battery)


my_tesla = ElectricCar('tesla','model s ',2016,50)
print(my_tesla.get_descriptive_name())
my_tesla.battery.describe_battery()

```


##### 输出结果：   
2016 Tesla Model S      
This car has a 70-kwh battery.  

``` python
class Car():
    """一次模拟汽车的简单尝试"""

    def __init__(self ,make, model, year):
        self.make = make
        self.model = model
        self.year = year
        self.odometer_reading = 0

    def get_descriptive_name(self):
        long_name = str(self.year) + ' ' + self.make + ' ' + self.model 
        return long_name.title()

    def read_odometer(self):
        print('This car has ' + str(self.odometer_reading) + ' miles on it.')

    def update_odometer(self,mileage):
        if mileage >= self.odometer_reading:
            self.odometer_reading = mileage
        else:
            print("You can't roll back an odometer!")

    def increment_odometer(self,miles):
        self.odometer_reading += miles

    
class Battery():
    """一次模拟电动汽车电瓶的简单尝试"""

    def __init__(self,battery_size=70):
        """初始化电瓶的属性"""
        self.battery_size = battery_size

    def describe_battery(self):
        """打印一条描述电瓶容量的消息"""
        print("This car has a " + str(self.battery_size) + "-kwh battery.")

    def get_range(self):
        """打印一条消息，指出电瓶的续航里程"""
        if self.battery_size == 70 :
            range = 240
        elif self.battery_size == 85:
            range = 270

        message = "This car can go approxiamately " + str(range)
        message += "miles on a full charge."
        print(message)


class ElectricCar(Car):
    """电动汽车的独特之处"""
    def __init__(self,make,model,year,battery):
        """
        初始化父类的属性，再初始化电动汽车特有的属性
        """
        super().__init__(make,model,year)
        self.battery = Battery(battery)


my_tesla = ElectricCar('tesla','model s ',2016,70)
print(my_tesla.get_descriptive_name())
my_tesla.battery.describe_battery()
my_tesla.battery.get_range()

```


##### 输出结果：   
2016 Tesla Model S     
This car has a 70-kwh battery.   
This car can go approxiamately 240miles on a full charge.   


##### 题目：
给Battery类添加一个名为upgrade_battery()的方法。这个方法检查电瓶容量，如果它不是85，就将它设置为85.创建一辆电瓶容量为默认值的电动车，调用方法get_range()，然后对电瓶进行升级，并再次调用get_range().你会看到这辆汽车的续航里程增加了。

``` python
class Car():
    """一次模拟汽车的简单尝试"""

    def __init__(self ,make, model, year):
        self.make = make
        self.model = model
        self.year = year
        self.odometer_reading = 0

    def get_descriptive_name(self):
        long_name = str(self.year) + ' ' + self.make + ' ' + self.model 
        return long_name.title()

    def read_odometer(self):
        print('This car has ' + str(self.odometer_reading) + ' miles on it.')

    def update_odometer(self,mileage):
        if mileage >= self.odometer_reading:
            self.odometer_reading = mileage
        else:
            print("You can't roll back an odometer!")

    def increment_odometer(self,miles):
        self.odometer_reading += miles

    
class Battery():
    """一次模拟电动汽车电瓶的简单尝试"""

    def __init__(self,battery_size=70):
        """初始化电瓶的属性"""
        self.battery_size = battery_size

    def describe_battery(self):
        """打印一条描述电瓶容量的消息"""
        print("This car has a " + str(self.battery_size) + "-kwh battery.")

    def get_range(self):
        """打印一条消息，指出电瓶的续航里程"""
        if self.battery_size == 70 :
            range = 240
        elif self.battery_size == 85:
            range = 270

        message = "This car can go approxiamately " + str(range)
        message += "miles on a full charge."
        print(message)

    def upgrade_battery(self):
        """检查电瓶容量"""
        if self.battery_size != 85:
            self.battery_size = 85


class ElectricCar(Car):
    """电动汽车的独特之处"""
    def __init__(self,make,model,year):
        """
        初始化父类的属性，再初始化电动汽车特有的属性
        """
        super().__init__(make,model,year)
        self.battery = Battery()


my_tesla = ElectricCar('tesla','model s ',2016)
my_tesla.battery.get_range()
my_tesla.battery.upgrade_battery()
my_tesla.battery.get_range()

```

##### 输出结果：    
This car can go approxiamately 240miles on a full charge.     
This car can go approxiamately 270miles on a full charge.   



