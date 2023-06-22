# 写作目的
MongoDB 作为一个开源文档数据库，凭借其灵活可扩展、分布式等优势，逐渐得到国内外越来越多开发者的青睐。经过十几年的发展，MongoDB 的生态越来越完善。在近几年的 [DB-Engines](https://db-engines.com/en/ranking) 排名中，MongoDB 稳居前五。

截至目前，关系型数据库仍然是学术界和工业界的主流，相信大学期间上过数据库课程的同学对 SQL、范式等概念都不陌生。NoSQL、文档数据库作为后起之秀并没有走进大多数人的视野，因此业界对其的分析和知识沉淀相对较少。

不少 MongoDB 开发者在查阅大量资料后明白了文档的概念，知道了如何配置分片表和负载均衡，并最终搞定了业务需求。但是在希望进一步了解 MongoDB 的底层原理时却步履维艰，不知道从哪里分析代码，如何真正了解 MongoDB 底层运行的来龙去脉。可能只能面对 MongoDB 100 多万行代码望洋兴叹（使用 [tokei](https://github.com/XAMPPRocky/tokei) 统计了 r4.0.28 和当前最新的 r7.0.0 版本，不含第三方库）。

几年前，我在机缘巧合之下接触了 MongoDB，然后又从事了国内云厂商 MongoDB 开发和运维工作。从一个没听过 MongoDB 名字的小白开始熟悉操作，了解它的基本原理和运作方式。但只是了解这些知识，距离真正掌控 MongoDB 还有很大差距。对我来说，曾经连续几小时处理一个线上问题而得不到根因，翻遍了 Google 也无济于事的场景记忆犹新。

于是，在后面的工作中主动熟悉 MongoDB 代码，分析社区 jira，做了很多的测试验证。在此过程中，自己记录很多的笔记和心得体会。现在通过 Github/Gitbook 进行总结，希望对学习 MongoDB 的开发者和运维人员有一定的帮助。

# 推荐的 MongoDB 学习资料
|参考文档|	链接|
|:--|:--|
|MongoDB 官方操作手册|	https://www.mongodb.com/docs/manual/|
|MongoDB Github Wiki|	https://github.com/mongodb/mongo/wiki|
|MongoDB 官方课程|	https://learn.mongodb.com/|
|MongoDB 中文社区|	https://mongoing.com/|
|MongoDB 官方设计文档|	https://github.com/mongodb/specifications/tree/master|
|WiredTiger 官方文档|	https://source.wiredtiger.com/3.2.1/index.html|
|WiredTiger Github Wiki|	https://github.com/wiredtiger/wiredtiger/wiki|
|一些中文电子书|	https://github.com/y123456yz/reading-and-annotate-mongodb-3.6/tree/master/%E6%96%87%E6%A1%A3%E5%8F%82%E8%80%83|

# 特别说明
1. MongoDB 官方已经提供了比较丰富的学习资料。因此，本书主要结合内核代码对 MongoDB 的核心模块进行深入分析，并尽量避免和业界现有的资料重复。另外会结合自身积累的 MongoDB 运营经验对 MongoDB 的使用场景提出一些解决方案；
2. MongoDB 内核版本的迭代速度很快，很多模块都会不断进行优化和重构，并增加新功能。因此，本书中涉及到的原理和代码分析会注明版本（以 4.0/4.2/4.4/5.0 为主），并给出对应的代码链接。如果引用了第 3 方的资料，也会通过链接注明出处；
3. 除非特别说明，书中的分析和测试都是基于 linux x86_64 架构；
4. 转载请注明出处；

# 作者
彭振翼、尹超