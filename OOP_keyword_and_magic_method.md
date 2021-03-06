2014/7/20
#OOP 关键字和魔术方法

###final: 
>用来标识类或类中的方法,用`final`标识的类不能被继承,用`final`标识的方法在子类中不能被覆盖

###static: 
>将类中的成员标识为静态,静态方法只能访问静态成员
####访问:
类中:self::属性名    self::方法名
类外:类名::属性名    类名::方法名


###单态设计模式:一个类只能有一个实例对象存在

    class DB {
    	private static $db = null;
    	
    	private function __construct() {
    		echo '连接数据库成功<br />';
    	}
    	
    	static function conn() {
    		if(is_null(self::$db)) {
    			return new self();    //实例化本类对象
    		}
    	}
    	
    	function query($sql) {
    		echo $sql;
    	}
    }
    $db = DB::conn();
    $db->query('select * from tables');
	
	
###const: 
>将类中属性定义为常量,常量名一般为大写且没有 "$" 符号
####访问:
类中:self::属性名
类外:类名::属性名

    class MyClass {
    	const CONSTANT = 'constant value';
    	
    	function showConstant() {
    		echo self::CONSTANT.'<br />';
    	}
    }
    echo MyClass::CONSTANT.'<br />';
    $class = new MyClass();
    $class->showConstant();
	
	
###instanceof: 
>确定一个对象是类的实例,类的子类,还是实现了某个特定的接口

    class Person {
    	protected $name;
    	protected $sex;
    	protected $age;
    	
    	function __construct($name, $sex, $age) {
    		$this->name = $name;
    		$this->sex = $sex;
    		$this->age = $age;
    	}
    	
    	public function say() {
    		echo '姓名:'.$this->name.' 性别:'.$this->sex.' 年龄:'.$this->age.'<br />';
    	}
    }
    $person = new Person('小明', '男', 25);
    if($person instanceof Person) {
    	echo '$person 是 Person 类的实例对象';
    }
	
	
###克隆对象:
>根据原有对象克隆出一个完全相同的对象,两个对象之间相互独立

    //直接克隆
    class Person {
    	protected $name;
    	protected $sex;
    	protected $age;
    	
    	function __construct($name, $sex, $age) {
    		$this->name = $name;
    		$this->sex = $sex;
    		$this->age = $age;
    	}
    	
    	public function say() {
    		echo '姓名:'.$this->name.' 性别:'.$this->sex.' 年龄:'.$this->age.'<br />';
    	}
    }
    $person = new Person('小明', '男', 25);
    $person2 = clone $person;
    $person->say();
    $person2->say();
        
    //克隆时使用 __clone() 重新赋初值
    class Person {
    	protected $name;
    	protected $sex;
    	protected $age;
    	
    	function __construct($name, $sex, $age) {
    		$this->name = $name;
    		$this->sex = $sex;
    		$this->age = $age;
    	}
    	
    	function __clone() {
    		$this->name = '小樱';
    		$this->sex = '女';
    		$this->age = '20';
    	}
    	
    	public function say() {
    		echo '姓名:'.$this->name.' 性别:'.$this->sex.' 年龄:'.$this->age.'<br />';
    	}
    }
    $person = new Person('小明', '男', 25);
    $person2 = clone $person;
    $person->say();
    $person2->say();
	
	
###`__toString()`: 
>是直接输出对象引用时直接调用的方法,执行函数内定义的功能


###`__call($functionName, $args)`: 
>当调用类中不存在的方法时自动调用,`$functionName`为不存在的函数名,`$args`为调用`$functionName`函数时使用的参数,是一个数组

    class Person {
    	protected $name;
    	protected $sex;
    	protected $age;
    	
    	function __construct($name, $sex, $age) {
    		$this->name = $name;
    		$this->sex = $sex;
    		$this->age = $age;
    	}
    	
    	function __call($functionName, $args) {
    		echo '你所调用的函数:'.$functionName.'() 不存在';
    	}
    	
    	public function say() {
    		echo '姓名:'.$this->name.' 性别:'.$this->sex.' 年龄:'.$this->age.'<br />';
    	}
    }
    $person = new Person('小明', '男', 25);
    $person->speak();
	
	
###自动加载类`__autoload()`: 
>当新建对象所调用的类不存在时自动调用

    function __autoload($filename) {
    	include($filename.'.php');
    }
        
    $person = new Person('小明', '男', 25);
    $person->say();

###对象串行化: 
####`serialize($obj)`: 
>将对象`$obj`转化为二进制字符串

####`unserialize($objString)`: 
>反串行化操作,还原对象

###`__sleep()`: 
>串行化自动调用,不需要参数,但需要返回一个数组,数组中的参数为串行化的参数,数组中不包含的参数串行化时自动忽略

###`__wakeup()`: 
>反串行化时自动调用,还原对象时为串行化忽略的参数重新赋值