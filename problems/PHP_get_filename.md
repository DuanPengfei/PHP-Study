2014/7/20
#PHP 获取当前文件的文件名

    //第一种
    $url = $_SERVER['PHP_SELF'];
    $filename = substr($url, strrpos($url, '/') + 1);
        
    //第二种
    $url = $_SERVER['PHP_SELF'];
    $arr = explode('/', $url);
    $filename = $arr[count($arr) - 1];
        
    //第三种
    $url = $_SERVER['PHP_SELF'];
    $arr = explode('/', $url);
    $filename = end($arr);