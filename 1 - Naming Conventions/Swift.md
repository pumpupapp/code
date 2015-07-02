## Conventions in naming functions 
(Follow the standard naming things convention excepting under these situations)

If you have a parameter to pass in, then use the standard getWhatever(param), setWhatever(param). However if you have no parameters to pass then you should use set{} and get{}. Swift has Setter & Getter syntax. Therefore all variables should be made private by the class and accessed with just .name syntax. The setter and getter should have the variable name without the underscrore.

```swift
class Car
{
    String _color = "RED"
    
    String color
    {
        set{_color = newValue}
        get{return _color}
    }
}

//And to access it

Car car = new Car()
car.color = "GREEN"
println(car.color)

```

<br />
