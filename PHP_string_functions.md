2014/8/4
#PHP 常用字符串处理函数
###`strlen($str)`: 
>计算字符串长度

    $str = 'Hello world';
    echo strlen($str);
	
	
###`str_replace(search, repalce, $str`): 
>字符串替换

    $str = 'Fuck you';
    $str = str_replace('Fuck', '***', $str);
    echo $str;
	
	
###`strtr($str, array('from'=>'to'))`: 
>根据多个条件替换,条件用数组传递

    $str = 'Fuck you,shit,bitch';
    $str = strtr($str, array('Fuck'=>'***', 'shit'=>'***', 'bitch'=>'***'));
    echo $str;
	
	
###`substr($str, start, length)`: 
>截取子字符串

    $str = 'tommow is another day';
    echo substr($str, 0, 3);    //从头开始,截取 3 个字符
    echo substr($str, 0, -3);    //从头开始,截至倒数 3 个字符
	
	
###`explode(delimiter, $str)`: 
>拆分字符串,拆分成数组

    $str = 'a, b, c';
    $arr = explode(',', $str);
    print_r($arr);
	
	
###`implode(array(), delimiter)`: 
>将数组拼接成字符串

    $str = 'a, b, c';
    $arr = explode(',', $str);
    $str = implode($arr, ',');
    echo $str;