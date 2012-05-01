# 重读C语言#
## C语言的那些事 ##

C语言是各大高校学习编程的入门语言。但作为入门语言，并不表示它是简单的。C语言的诞生是和UNIX操作系统密切相关的（一般说来，如果没用过UNIX/类UNIX操作系统，几乎不能认为那个人懂计算机），历史上很难分清到底是先有UNIX还是现有C（有点像先有鸡还是先有蛋的问题）。C语言是最接近底层特性的高级语言，但比汇编语言要好用地多。之前因为CPU编程空间的限制，人们迫不得已采用汇编进行编程。现在，在ARM的平台上已经能够获得C++的编译支持。STM8也有人专门做了程序的C++封装。不过现在嵌入式平台上的C++实现也颇有点像几十年前的C++，即C with class，着重使用类特性。事实上，PC上的C++语言经过这几十年来的发展，已经变得很不一样了。

下面两篇博文，可以用来检验自己C语言是否真正掌握。地址分别是<http://coolshell.cn/articles/945.html>，还有<http://coolshell.cn/articles/873.html>，希望他们能给你带来深入的思考。当然，如果今后要走程序员的道路，类似的这些问题在今后的面试中一定能碰得到（无论是别人面你还是你面别人）。

以下是从上述两篇博文中摘出来的5个问题，答案我会直接列在第五个问题后面，至于为什么，自己去网站找吧！Enjoy it!
1.下面的程序会输出什么？
    #include <stdio.h>
    int main() 
    {
        float a = 12.5;
        printf("%d\n", a); 
        printf("%d\n", (int)a); 
        printf("%d\n", *(int *)&a); 
        return 0; 
    }

    
2.下面，我们再来看一个交叉编译的事情，下面的两个文件可以编译通过吗？如果可以通过，结果是什么？
file1.c 
    int arr[80]; 

file2.c 
extern int *arr;
int main() 
{
    arr[1] = 100;
    printf("%d\n", arr[1]);
    return 0; 
} 


3.请问下面的程序输出什么？
#include <stdio.h> 
int main() 
{
    int i;
    i = 10;
    printf("i : %d\n",i);
    printf("sizeof(i++) is: %d\n",sizeof(i++));
    printf("i : %d\n",i);
    return 0; 
}


4.下面这个函数返回值是什么？
    int x = 5;
    int f() {
      int x = 3;
      {
        extern int x;
        return x;
      }
    }

5.下面的语句哪些是合法的？
    int (*pf)(void);
    int f(void)
    {

       pf = &f; // 没问题
       pf = ***f; // 取址？
       pf(); // 函数指针可以调用？
       (****pf)();  // 这又是什么？
       (***************f)(); // 这个够变态了吧？
    }

下面是答案：
第一题：
    0
    12
    1095237632
第二题：
    该程序可以编译通过，但运行时会出错。
第三题：
    10，4，10
第四题：
    5
第五题：
    全部合法。


C语言不乏一些蛋疼的比赛，去看看[国际C语言混乱代码大赛](http://www0.us.ioccc.org/years.html)吧,你能看到这样的代码：

		                               /*
		                              +
		                             +
		                            +
		                            +
		                            [         >i>n[t
		                             */   #include<stdio.h>
		                /*2w0,1m2,]_<n+a m+o>r>i>=>(['0n1'0)1;
		             */int/**/main(int/**/n,char**m){FILE*p,*q;int        A,k,a,r,i/*
		           #uinndcelfu_dset<rsitcdti_oa.nhs>i/_*/;char*d="P%"   "d\n%d\40%d"/**/
		         "\n%d\n\00wb+",b[1024],y[]="yuriyurarararayuruyuri*daijiken**akkari~n**"
		  "/y*u*k/riin<ty(uyr)g,aur,arr[a1r2a82*y2*/u*r{uyu}riOcyurhiyua**rrar+*arayra*="
	       "yuruyurwiyuriyurara'rariayuruyuriyuriyu>rarararayuruy9uriyu3riyurar_aBrMaPrOaWy^?"
	      "*]/f]`;hvroai<dp/f*i*s/<ii(f)a{tpguat<cahfaurh(+uf)a;f}vivn+tf/g*`*w/jmaa+i`ni("/**
	     */"i+k[>+b+i>++b++>l[rb";int/**/u;for(i=0;i<101;i++)y[i*2]^="~hktrvg~dmG*eoa+%squ#l2"
	     ":(wn\"1l))v?wM353{/Y;lgcGp`vedllwudvOK`cct~[|ju {stkjalor(stwvne\"gt\"yogYURUYURI"[
	     i]^y[i*2+1]^4;/*!*/p=(n>1&&(m[1][0]-'-'||m[1][1]  !='\0'))?fopen(m[1],y+298):stdin;
	      /*y/riynrt~(^w^)],]c+h+a+r+*+*[n>)+{>f+o<r<(-m]    =<2<5<64;}-]-(m+;yry[rm*])/[*
	       */q=(n<3||!(m[2][0]-'-'||m[2][1]))?stdout /*]{     }[*/:fopen(m[2],d+14);if(!p||/*
	       "]<<*-]>y++>u>>+r >+u+++y>--u---r>++i+++"  <)<      ;[>-m-.>a-.-i.++n.>[(w)*/!q/**/)
	    return+printf("Can "  "not\x20open\40%s\40"    ""       "for\40%sing\n",m[!p?1:2],!p?/*
	  o=82]5<<+(+3+1+&.(+  m  +-+1.)<)<|<|.6>4>-+(>    m-        &-1.9-2-)-|-|.28>-w-?-m.:>([28+
	 */"read":"writ");for  (   a=k=u= 0;y[u];  u=2    +u){y[k++   ]=y[u];}if((a=fread(b,1,1024/*
	,mY/R*Y"R*/,p/*U*/)/*          R*/ )>/*U{  */   2&& b/*Y*/[0]/*U*/=='P' &&4==/*"y*r/y)r\}
	*/sscanf(b,d,&k,& A,&           i,  &r)&&        !   (k-6&&k -5)&&r==255){u=A;if(n>3){/*
	]&<1<6<?<m.-+1>3> +:+ .1>3+++     .   -m-)      -;.u+=++.1<0< <; f<o<r<(.;<([m(=)/8*/
	u++;i++;}fprintf   (q,    d,k,           u      >>1,i>>1,r);u  = k-5?8:4;k=3;}else
	  /*]>*/{(u)=/*{   p> >u  >t>-]s                >++(.yryr*/+(    n+14>17)?8/4:8*5/
	     4;}for(r=i=0  ;  ;){u*=6;u+=                (n>3?1:0);if    (y[u]&01)fputc(/*
	      <g-e<t.c>h.a r  -(-).)8+<1.                 >;+i.(<)<     <)+{+i.f>([180*/1*
	      (r),q);if(y[u   ]&16)k=A;if                               (y[u]&2)k--;if(i/*
	      ("^w^NAMORI; {   I*/==a/*"                               )*/){/**/i=a=(u)*11
	       &255;if(1&&0>=     (a=                                 fread(b,1,1024,p))&&
		")]i>(w)-;} {                                         /i-f-(-m--M1-0.)<{"
		 [ 8]==59/* */                                       )break;i=0;}r=b[i++]
		    ;u+=(/**>>                                     *..</<<<)<[[;]**/+8&*
		    (y+u))?(10-              r?4:2):(y[u]         &4)?(k?2:4):2;u=y[u/*
		     49;7i\(w)/;}             y}ru\=*ri[        ,mc]o;n}trientuu ren (
		     */]-(int)'`';}             fclose(          p);k= +fclose( q);
		      /*] <*.na/m*o{ri{                       d;^w^;}  }^_^}}
		       "   */   return  k-                -1+   /*\'   '-`*/
		             (   -/*}/   */0x01        );       {;{    }}
		                    ;           /*^w^*/        ;}

P.S.不用怀疑这段程序是否能够通过编译，这是一个图像降采样的工具。具体使用说明参见<http://www0.us.ioccc.org/2011/akari/hint.text>。我想说的是，维护这样的代码真是坑爹啊！

## 声明与定义 ##

## 关于union ##


## 悬垂else ##

## static的作用 ##


## 断言之美 ##





关于进一步学习C语言的资料，我这里推荐下列三本书：[《C程序设计语言》](http://product.china-pub.com/14975&ref=browse)、[《C专家编程》]http://product.china-pub.com/38005)、[《C陷阱与缺陷》](http://product.china-pub.com/38125)。一般来说，以《C程序设计语言》为基础，然后凭借后面两本书，知道C语言平时使用中一些容易犯错的地方。当然，如果你觉得还不够的话，以下这篇文章可能会适合你：[如何学好C语言](http://coolshell.cn/articles/4102.html)。




 
