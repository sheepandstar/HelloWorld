### 一、给属性指定默认值


``` python
class Car():
    
    def __init__(self,make,model,year):
        """初始化描述汽车的属性"""
        self.make = make
        self.model = model
        self.year = year
        self.odometer_reading = 0

    def get_descriptive_name(self):
        """返回整洁的描述性信息"""
        long_name = str(self.year) + ' ' + self.make + ' ' + self.model
        return long_name.title()
    
    def read_odometer(self):
        """打印一条指出汽车里程的消息"""
        print("This car has " + str(self.odometer_reading) + " miles on it.")

my_new_car = Car('audi','a4',2016)
print(my_new_car.get_descriptive_name())
my_new_car.read_odometer()

```



##### 输出结果：    
2016 Audi A4   
This car has 0 miles on it.      


##### 注意：  
1. 类中的每个属性都必须有初始值，哪怕这个值是0或者空字符串。当给属性指定默认值时，在方法__init__()内指定这种初始值是可行的；如果我们对某个属性这样做了，就无需包含为它提供初始值的形参。


### 二、修改属性的值
##### 1. 直接修改属性的值：
通过实例直接访问它。如：将里程数读数设置为23.

``` python 
class Car():
    
    def __init__(self,make,model,year):
        """初始化描述汽车的属性"""
        self.make = make
        self.model = model
        self.year = year
        self.odometer_reading = 0

    def get_descriptive_name(self):
        """返回整洁的描述性信息"""
        long_name = str(self.year) + ' ' + self.make + ' ' + self.model
        return long_name.title()
    
    def read_odometer(self):
        """打印一条指出汽车里程的消息"""
        print("This car has " + str(self.odometer_reading) + " miles on it.")

my_new_car = Car('audi','a4',2016)
print(my_new_car.get_descriptive_name())

my_new_car.odometer_reading = 23
my_new_car.read_odometer()
```


##### 输出结果：  
2016 Audi A4    
This car has 23 miles on it.    

##### 2. 通过方法修改属性的值
如：创建方法update_odometer()的方法：
``` python
class Car():
    
    def __init__(self,make,model,year):
        """初始化描述汽车的属性"""
        self.make = make
        self.model = model
        self.year = year
        self.odometer_reading = 0

    def get_descriptive_name(self):
        """返回整洁的描述性信息"""
        long_name = str(self.year) + ' ' + self.make + ' ' + self.model
        return long_name.title()
    
    def read_odometer(self):
        """打印一条指出汽车里程的消息"""
        print("This car has " + str(self.odometer_reading) + " miles on it.")

    def update_odometer(self,mileage):
        """将里程表读数设置为指定值"""
        self.odometer_reading = mileage

my_new_car = Car('audi','a4',2016)
print(my_new_car.get_descriptive_name())

my_new_car.update_odometer(50)
my_new_car.read_odometer()
```

##### 输出结果：  
2016 Audi A4      
This car has 50 miles on it.    


##### 3. 通过方法对属性的值进行递增
有时候需要将属性值递增特定的量，而不是将其设置为全新的值。如：里程数增加100

``` python
class Car():
    
    def __init__(self,make,model,year):
        """初始化描述汽车的属性"""
        self.make = make
        self.model = model
        self.year = year
        self.odometer_reading = 0

    def get_descriptive_name(self):
        """返回整洁的描述性信息"""
        long_name = str(self.year) + ' ' + self.make + ' ' + self.model
        return long_name.title()
    
    def read_odometer(self):
        """打印一条指出汽车里程的消息"""
        print("This car has " + str(self.odometer_reading) + " miles on it.")

    def update_odometer(self,mileage):
        """将里程表读数设置为指定值"""
        self.odometer_reading = mileage

    def increment_odometer(self,miles):
        """将里程表读数增加指定的量"""
        self.odometer_reading += miles

my_used_car = Car('subaru','outback',2013)
print(my_used_car.get_descriptive_name())

my_used_car.update_odometer(23500)
my_used_car.read_odometer()

my_used_car.increment_odometer(100)
my_used_car.read_odometer()

```


##### 输出结果：  
2013 Subaru Outback   
This car has 23500 miles on it.    
This car has 23600 miles on it.    



