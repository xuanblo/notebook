# perl

## 数组
```perl
my @arr = (); # 定义数组
push @arr,"item1"; # 压入数组最后
pop 弹出元素
shift 左边弹出元素
unshift 左边压入元素
```

## hash哈希
```perl
my %hash = (
    "key1" => ['a', 'b'], # 哈希的数组
    "key2" => "item",
    "key3" => (           # 二维哈希
        'kkey1' => [1, 2 ,3],
        'kkey2' => [1, 2]
        )
    );

# 遍历哈希, 对key, value排序
foreach my $key (sort{$a cmp $b} keys %hash)
{
    # 按key值字符排序
}
foreach my $key (sort{$a <=> $b} keys %hash)
{
    # 按key值数字排序
}
foreach my $key (sort{$hash{$a} <=> $hash{$b}} keys %hash)
{
    # 按value值数字排序
}

```

## perl单行执行


## 判断文件是否为空，是否存在
* 判断文件是否存在 `if(-e $file_path){print "yes";}else{print "NO";}`
* 判断文件是否为空 `if((stat $file_path)[7]){print "yes";}else{print "NO";}`