#lec9 虚存置换算法spoc练习

## 个人思考题
1. 置换算法的功能？

2. 全局和局部置换算法的不同？

3. 最优算法、先进先出算法和LRU算法的思路？

4. 时钟置换算法的思路？

5. LFU算法的思路？

6. 什么是Belady现象？

7. 几种局部置换算法的相关性：什么地方是相似的？什么地方是不同的？为什么有这种相似或不同？

8. 什么是工作集？

9. 什么是常驻集？

10. 工作集算法的思路？

11. 缺页率算法的思路？

12. 什么是虚拟内存管理的抖动现象？

13. 操作系统负载控制的最佳状态是什么状态？

## 小组思考题目

----
(1)（spoc）请证明为何LRU算法不会出现belady现象  
设物理页数较少时算法维护的栈为S，物理页数增加后算法维护的栈为S'，则  
只需证明在任意时刻S总是S'的子集，则在任意时刻均不会出现在S中命中，在S'中缺失的情形，故缺页率不会上升，即不会出现belady现象。  
以下证明其加强命题：在任意时刻S总是S'的子集，且S与S'中相同元素的相对前后关系一致。  
1. 初始时，S、S'均为空，命题成立。  
2. 假设在t-1时刻命题成立，则在t时刻，被访元素有以下4种可能：  
   (1)在S、S'中均命中，则S、S'均将该元素调到栈底，S依然是S'的子集，两个栈中各元素相对关系依然一致，命题依然成立。  
   (2)在S中命中，在S'中缺失，则因为S是S'的子集，因而此情形不可能发生。  
   (3)在S中缺失，在S'中命中，则S将该元素加至栈底并弹出栈顶，S'将该元素移至栈底，易知原命题依然成立。  
   (4)在S、S'中均缺失，则S、S'均将该元素加至栈底，并弹出当前栈顶。因为S、S'中元素相对位置一致，故S'栈顶元素不可能为S非栈顶元素，而是与S栈顶元素相同或不在S栈中，可知两种情况下，原命题均保持成立。  
综上，由数学归纳法原理，在任意时刻S总是S'的子集，且S与S'中相同元素的相对前后关系一致。  
所以，在任意时刻均不会出现在S中命中，在S'中缺失的情形，S'缺页率不会大于S，即LRU算法不会出现belady现象。  



(2)（spoc）根据你的`学号 mod 4`的结果值，确定选择四种替换算法（0：LRU置换算法，1:改进的clock 页置换算法，2：工作集页置换算法，3：缺页率置换算法）中的一种来设计一个应用程序（可基于python, ruby, C, C++，LISP等）模拟实现，并给出测试。请参考如python代码或独自实现。
 - [页置换算法实现的参考实例](https://github.com/chyyuu/ucore_lab/blob/master/related_info/lab3/page-replacement-policy.py)
 
## 扩展思考题
（1）了解LIRS页置换算法的设计思路，尝试用高级语言实现其基本思路。此算法是江松博士（导师：张晓东博士）设计完成的，非常不错！

参考信息：

 - [LIRS conf paper](http://www.ece.eng.wayne.edu/~sjiang/pubs/papers/jiang02_LIRS.pdf)
 - [LIRS journal paper](http://www.ece.eng.wayne.edu/~sjiang/pubs/papers/jiang05_LIRS.pdf)
 - [LIRS-replacement ppt1](http://dragonstar.ict.ac.cn/course_09/XD_Zhang/(6)-LIRS-replacement.pdf)
 - [LIRS-replacement ppt2](http://www.ece.eng.wayne.edu/~sjiang/Projects/LIRS/sig02.ppt)
