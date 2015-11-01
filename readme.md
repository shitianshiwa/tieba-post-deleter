百度贴吧删贴机, 
由 [iamunknown](http://tieba.baidu.com/home/main?un=iamunknown)(即本人) 原来为minecraft吧所写

* 2014年10月 完成第一版
* 2015年2月 完全推倒重写, 框架基本固定
* 2015年6月 暂时停止维护 (到目前(2015年<del>9月26日</del>11月1日)为止,依旧能正常使用)

本打算加入lua支持(甚至作为主要框架),但迫于没有时间就搁置了.

默认每秒扫描主页,据此找到新贴子.

以下是大体的流程,细节将不阐述:

1. 如果发现主页主题列表有变化,且变化的时间大于等于上次扫描的时间,
2. 先会确认是否为新的主题, 若主题不是新的, 会检查该主题最后一楼;
3. 若最后一楼不是新的(这也有可能是百度还没有加上), 会通过高级搜索查找发贴人在本吧的最新发贴, 到这里依旧是瞬间的事;
4. 百度的高级搜索在特定的时间段, 贴子的更新会产生较长的延后, 所以若高级搜索未找到, 会加入延时查找;
5. 如果延时查找达到超过一定的次数(每次查找间隔的时间会越来越大)却依旧没找到, 才将会放弃.

测试了一下, 2015年9月26日, minecraft吧的关注有90万,
在CPU是`AMD Phenom(羿龙) II X4 965 四核`, 系统是`Windows 10 64位`的电脑下,
* 网络活动约10KB/s~20KB/s.
* CPU占用平均0.20%. 当年在我最低配的阿里云主机上, 也只有1~2%而已.
* 内存大约16MB. 曾连续稳定运行几百小时, 未出现内存泄露.
测试过程中除因没有吧务权限无法删贴, 未有任何异常.

相关模块:
https://github.com/Purstal/go-tieba-modules/tree/master/forum-page-monitor
https://github.com/Purstal/go-tieba-modules/tree/master/post-finder