### 第一题  
将两个递增的有序链表合并为一个递增的有序链表。要求结果链表仍使用原来两个链表的存储空间，不另外占用其他的存储空间。表不允许有重复的数据  
```
void MergeList(LinkList &La, LinkList &Lb, LinkList &Lc)      
{//将两个递增的有序链表La和Lb合并为一个递增的有序链表Lc
    pa = La->next;              //pa是链表La的工作指针，初始化为首元结点
    pb = Lb->next;              //pb是链表Lb的工作指针，初始化为首元结点
    //pa和pb分别是链表La和Lb的工作指针，初始化为相应链表的首元结点
    pc = Lc = La;               //用La的头结点作为Lc的头结点  
    while (pa && pb)            //用两个链表La和Lb均未到达表尾结点
    {
        if (pa->data < pb->data)
        {//取较小者La中的元素，将pa链接在pc的后面，pa指针后移
            pc->next = pa;
            pc = pa;
            pa = pa->next;
        }
        else if(pa->data > pb->data)
        {//取较小者Lb中的元素，将pb链接在pc的后面，pb指针后移
            pc->next = pb;
            pc = pb;
            pb = pb->next;
        }else
        {//相等时取La中的元素，删除Lb中的元素
            pc->next = pa;
            pc = pa;
            pa = pa->next;
            q = pb->next;
            delete pb;
            pb = q;
        }
    }
    pc->next = pa ? pa : pb;    //将非空表的剩余元素直接连接在Lc表的最后
    delete Lb;                  //释放Lb的头结点
}
```

new branch
