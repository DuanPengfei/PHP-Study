2014/7/17
#PHP 数组与数据结构 1

>`print_r($arr);`    //输出数组`$arr`中所有元素的下标和值
`var_dump($arr);`    //输出数组`$arr`中所有元素的下标和值,同时输出每个元素的类型

###定义数组

    $arr = array(
    	"市场部" => array(
    		array(1, "高某", "市场部经理", 5000.00),
    		array(2, "洛某", "职员", 3000.00),
    		array(3, "峰某", "职员", 2400.00)
    	),
    	"产品部" => array(
    		array(1, "高某", "产品部经理", 5000.00),
    		array(2, "洛某", "职员", 3000.00),
    		array(3, "峰某", "职员", 2400.00)
    	),
    	"财务部" => array(
    		array(1, "高某", "财务部经理", 5000.00),
    		array(2, "洛某", "职员", 3000.00),
    		array(3, "峰某", "职员", 2400.00)
    	)
    );


###遍历数组
####for: 
>遍历的数组必须是连续的索引数组,所以`for`循环遍历数组在 PHP 中不常用

    //一维数组
    $arr = array('a', 'b', 'c', 'd', 'e');
    echo '<table border="1" width="600">';
    echo '<tr>';
    for($i = 0; $i < count($arr); $i++) {
    	echo '<td>'.$arr[$i].'</td>';
    }
    echo '</tr>';
    echo '</table>';
        
    //二维数组
    $arr = array(
    	array(1, '高某', 'A公司', '北京市', '123456', 'a@123.com'),
    	array(2, '洛某', 'B公司', '上海市', '123456', 'b@123.com'),
    	array(3, '峰某', 'C公司', '杭州市', '123456', 'c@123.com')
    );
    echo '<table border="1" width="600">';
    for($row = 0; $row < count($arr); $row++) {
    	echo '<tr>';
    	for($col = 0; $col < count($arr[$row]); $col++) {
    		echo '<td>'.$arr[$row][$col].'</td>';
    	}
    	echo '</tr>';
    }
    echo '</table>';

####foreach: 

    //一维数组
    $arr = array('a', 'b', 'c', 'd', 'e');
    echo '<table border="1" width="600">';
    echo '<tr>';
    foreach($arr as $v) {
    	echo '<td>'.$v.'</td>';
    }
    echo '</tr>';
    echo '</table>';
        
    $arr = array('a', 'b', 'c', 'd', 'e');
    echo '<table border="1" width="600">';
    echo '<tr>';
    foreach($arr as $k => $v) {
    	echo '<td>'.$k.'=>'.$v.'</td>';
    }
    echo '</tr>';
    echo '</table>';
        
    //二维数组
    $arr = array(
    	array(1, '高某', 'A公司', '北京市', '123456', 'a@123.com'),
    	array(2, '洛某', 'B公司', '上海市', '123456', 'b@123.com'),
    	array(3, '峰某', 'C公司', '杭州市', '123456', 'c@123.com')
    );
    echo '<table border="1" width="600">';
    foreach($arr as $vOne) {
    	echo '<tr>';
    	foreach($vOne as $vTwo) {
    		echo '<td>'.$vTwo.'</td>';
    	}
    	echo '</tr>';
    }
    echo '</table>';
        
    $arr = array(
    	array(1, '高某', 'A公司', '北京市', '123456', 'a@123.com'),
    	array(2, '洛某', 'B公司', '上海市', '123456', 'b@123.com'),
    	array(3, '峰某', 'C公司', '杭州市', '123456', 'c@123.com')
    );
    echo '<table border="1" width="600">';
    foreach($arr as $kOne => $vOne) {
    	echo '<tr>';
    	foreach($vOne as $kTwo => $vTwo) {
    		echo '<td>'.$kTwo.'=>'.$vTwo.'</td>';
    	}
    	echo '</tr>';
    }
    echo '</table>';


####each: 
>each每次向后移动一位,返回包含 4 个元素的数组,其中键名 0 ,`key`对应原数组中的键名,键名 1 ,`value`对应原数组中的键值,数组越界时返回布尔值`false`,当`each`循环完数组后指针已经移到数组尾部,想要重新循环输出数组要使用`reset()`函数,而`foreach`则会循环后自动返回到数组首部

    $arr = array('ID' => 1, '姓名' => '高某', '公司' => 'A公司', '地址' => '北京市');
    $ID = each($arr);
    print_r($ID);
    $name = each($arr);
    print_r($name);
    $company = each($arr);
    print_r($company);
    $adderss = each($arr);
    print_r($adderss);
    $no = each($arr);
    var_dump($no);


####list: 
>将数组中的值赋值给 list 中对应的参数,然后以变量的方式输出

    $arr = array(1, '高某', 'A公司', '北京市');
    list($ID, $name, $company, $adderss) = $arr;
    echo $ID.' '.$name.' '.$company.' '.$adderss;


####each,list联用: 

    $arr = array('ID' => 1, '姓名' => '高某', '公司' => 'A公司', '地址' => '北京市');
    list($key, $value) = each($arr);
    echo $key.'=>'.$value;


####while: 

    $arr = array('ID' => 1, '姓名' => '高某', '公司' => 'A公司', '地址' => '北京市');
    while(list($key, $value) = each($arr)) {
    	echo $key.'=>'.$value;
    }

	
####数组内部指针
>`current()`取得当前指针的内容,`key()`取得当前指针的索引,`next()`指针移动到下一个单元,`prev()`指针倒回一位,`end()`指针移动到数组尾部,`reset()`指针移动到数组首部

    $arr = array('ID' => 1, '姓名' => '高某', '公司' => 'A公司', '地址' => '北京市');
    echo key($arr).'=>'.current($arr);
    next($arr);
    echo key($arr).'=>'.current($arr);
    end($arr);
    echo key($arr).'=>'.current($arr);
    reset($arr);
    echo key($arr).'=>'.current($arr);