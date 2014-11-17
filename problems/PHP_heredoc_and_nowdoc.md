
2014/8/4
#PHP 中 heredoc 和 nowdoc 处理大段内容
>`heredoc`相当于单引号,`nowdoc`相当于双引号,标记符结尾必须顶格写,不能有空格或 Tab,且标记符结尾有分号

###heredoc

        $str = <<<TEST
        This is the test content.
    TEST;

###nowdoc

        $str = <<<'TEST'
        This is the test content.
    TEST;