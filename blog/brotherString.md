#如何快速在字典中找到兄弟字符串
###背景
前段时间面试的时候，面试官问了我这个问题  
当时的直接想法是类似hash的实现方式，把每个string排序后作为key算出一个value  
只不过算value的方法上想到了加法（不行）和乘法（素数可以，但没有想到），结果都不行。  
然后就描述了一个O(n^2)的笨方法。  
接着面试官又问我有没有O(n)的方法，我说不会（T_T），然后估计面试就黄了。。。  
回头想想，挺可惜的，只有现在重新捡回来诶。  
###实现
平时习惯用js来写，找找underscore发现里面木有hash()，就准备自己写个  
网上找找，发现了一个简单又好用的哈希算法times33  
```
    function hash_times33(value,bucket){
        if(!value||typeof (value) !== "string") return;
        var bucket = bucket || 500; //设置bucket默认长度
        var result = 0;
        for(var i=0;i<value.length;i++){
            result=(result*33 + value.charCodeAt(i))%bucket
        }
        return result;
    }
```
算法挺简单的也挺好理解  
有了这个function再来找兄弟字符串就简单多了  
诶，可惜，当时知道就好了  

PS:发现貌似少了个排序string的方法，现在补充上去  

```
    function sort_str(str){
        return str.split("").sort().join("");
    }
```

