2014/7/20
#PHP 魔术方法

###OOP 中的魔术方法
####__set(): 
>在为私有属性赋值时自动调用
声明: void __set(string name, mixed value)

    class Person {
    	private $name;
    	private $sex;
    	private $age;
    	
    	function __construct($name, $sex, $age) {
    		$this->name = $name;
    		$this->sex = $sex;
    		$this->age = $age;
    	}
    	
    	function __set($propertyName, $propertyValue) {
    		if($propertyName == "sex") {
    			if(!($propertyValue == "男" || $propertyValue == "女")) {
    				return;
    			}
    		}
    		
    		if($propertyName == "age") {
    			if($propertyValue >150 || $propertyValue < 0) {
    				return;
    			}
    		}
    		
    		$this->$propertyName = $propertyValue;
    	}
    	
    	public function say() {
    		echo '姓名:'.$this->name.' 性别:'.$this->sex.' 年龄:'.$this->age.'<br />';
    	}
    }
    $person = new Person('小明', '男', 35);
    $person->say();
    $person->name = '小樱';
    $person->sex = '女';
    $person->age = 20;
    $person->say();
	
	
####__get()
>声明:mixed __get(string name)

    class Person {
    	private $name;
    	private $sex;
    	private $age;
    	
    	function __construct($name, $sex, $age) {
    		$this->name = $name;
    		$this->sex = $sex;
    		$this->age = $age;
    	}
    	
    	function __get($propertyName) {
    		if($propertyName == 'sex') {
    			return '保密';
    		}	else if($propertyName == 'age') {
    				if($this->age > 30) {
    					return $this->age - 5;
    				}
    				else {
    					return $this->age;
    				}
    			}
    			else {
    				return $this->$propertyName;
    			}
    	}
    }
    $person = new Person('小明', '男', 35);
    echo '姓名:'.$person->name.' 性别:'.$person->sex.' 年龄:'.$person->age.'<br />';
	
	
####__isset(): 
>判断是否存在该属性
声明:bool __isset(string name)
	
####__unset(): 
>删除该属性
声明:void __unset(string name)