2014/7/18
#PHP 数组与数据结构 2

###预定义数组
####服务器变量: $_SERVER

    foreach($_SERVER as $key => $value) {
    	echo '$_SERVER['.$key.'] = '.$value.'<br />';
    }
    echo '<pre>';
    print_r($_SERVER);
    echo '</pre>';
	
####环境变量: $_ENV

    foreach($_ENV as $key => $value) {
    	echo '$_ENV['.$key.'] = '.$value.'<br />';
    }
	
####URL GET 变量: $_GET
>获取`URL`或表单的`GET`方式传递过来的参数

    //$url = localhost/test.php?action=1&user=shawn&id=10&page=5;
    echo '参数 action 为:'.$_GET['action'].'<br />';
    echo '参数 user 为:'.$_GET['user'].'<br />';
    echo '参数 id 为:'.$_GET['id'].'<br />';
    echo '参数 page 为:'.$_GET['page'].'<br />';
    echo '<pre>';
    print_r($_GET);
    echo '</pre>';
	
	
####HTTP POST 变量: $_POST

    foreach($_POST as $key => $value) {
    	echo $key.':'.$value.'<br />';
    }
    <html>
    	<head>
    		<title>添加联系人</title>
    	</head>
    	<body>
    		<form action="" method="post">
    			编号:<input type="text" name="id"><br />
    			姓名:<input type="text" name="name"><br />
    			公司:<input type="text" name="company"><br />
    			地址:<input type="text" name="address"><br />
    			电话:<input type="text" name="phone"><br />
    			EMAIL:<input type="text" name="email"><br />
    			<input type="submit" value="添加新联系人">
    		</form>
    	<body>
    </html>
	
	
####request 变量: 
>`$_REQUEST`包含`$_POST`,`$_GET`,`$_COOKIE`中的全部内容,不管`POST`还是`GET`方法提交的数据都能用`REQUEST`来获取.但是`REQUEST`速度较慢,不建议使用
	
####HTTP 文件上传变量: $_FILES
	
####HTTP Cookies: $_COOKIE
	
####Session 变量: $_SESSION
	
####Global 变量: $_GLOBALS
>是由所有已定义的全局变量组成的数组，变量名就是数组的索引,在函数中可替代`global`

    $a = 1;
    $b = 2;
    function sum() {
    	$GLOBALS['b'] = $GLOBALS['a'] + $GLOBALS['b'];
    }
    sum();
    echo $b;

####数组的相关处理函数: 此部分内容在项目中学习,随用随学