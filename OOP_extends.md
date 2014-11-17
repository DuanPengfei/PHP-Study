2014/7/20
#OOP 继承性

    //继承
    class Person {
    	protected $name;
    	protected $sex;
    	protected $age;
    	
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
    	
    	public function say() {
    		echo '姓名:'.$this->name.' 性别:'.$this->sex.' 年龄:'.$this->age.'<br />';
    	}
    }
        
    //Student 继承 Person
    class Student extends Person {
    	private $school;
    	
    	//重载构造函数
    	function __construct($name, $sex, $age, $school){
    		parent::__construct($name, $sex, $age);
    		$this->school = $school;
    	}
    	
    	//重载 say 函数
    	function say(){
    		parent::say();
    		echo ' 学校:'.$this->school.'<br />';
    	}
    }
    $person = new Person('小明', '男', 35);
    $person->say();
    $student = new Student('小樱', '女', 20, 'HDU');
    $student->say();