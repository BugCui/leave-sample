# leave-sample
一、说明

本代码源于极客时间《DDD实战课》，DDD知识体系和代码详解可参考专栏。

在《DDD实战课》专栏第18节中我们用事件风暴完成了“在线请假考勤”项目的领域建模和微服务设计。
我们一起从程序员的视角去看看用DDD方法设计和开发出来的微服务代码到底是什么样的？

二、项目回顾

“在线请假考勤”项目中，请假的核心业务流程是：“请假人填写请假单提交审批。根据请假人身份、请假类型和请假天数进行校验并确定审批规则。根据审批规则确定审批人，逐级提交上级审批，逐级核批通过则完成审批，否则审批不通过则退回申请人。”

在第18节的DDD领域建模和微服务设计中，我们已经拆分出了两个微服务：请假和考勤微服务。
本部分是请假微服务的示例代码，采用的开发语言和数据库分别是：Java、Spring boot和PostgreSQL。

三、请假微服务采用的DDD设计思想

请假微服务中用到了很多DDD设计思想和方法，主要包括以下几点。

1.聚合的管理：聚合根、实体和值对象的关系。

2.聚合数据的初始化和持久化：工厂和仓储模式。

3.聚合的解耦：聚合代码的解耦、跨聚合的服务调用和对象解耦。

4.领域事件管理：领域事件实体结构、持久化和事件发布。

5.DDD分层架构：基础层、领域层、应用层和用户接口层的协作。

6.服务的分层与协作：实体方法、领域服务、应用服务、接口服务，服务的组合和编排，跨多个聚合的服务管理和协同。

7.对象的分层和转换：DTO、DO和PO等对象在不同层的转换和实现过程。

8.微服务之间的访问：登录和认证服务。

# DDD

---

## DDD基本概念

* [DDD驱动领域设计](https://blog.csdn.net/wwd0501/article/details/95062535/)

## leave-sample

Interfaces 『接口层』：

* Facade: api
* Dto: 传输实体
* assembler：转换器

Applicaion.Service『聚合层』:

* feign 远程调用
* domain 服务调用

Doamin『领域层』⭐ :

* leave 领域模型

Infrastructure『基础架构层』:

* util 工具

领域划分：

leave、person、rule



![软件架构模式的演进](https://raw.githubusercontent.com/BugCui/picBed/main/%E8%BD%AF%E4%BB%B6%E6%9E%B6%E6%9E%84%E6%A8%A1%E5%BC%8F%E7%9A%84%E6%BC%94%E8%BF%9B.jpg)



![DDD分层架构与微服务代码模型](https://raw.githubusercontent.com/BugCui/picBed/main/DDD%E5%88%86%E5%B1%82%E6%9E%B6%E6%9E%84%E4%B8%8E%E5%BE%AE%E6%9C%8D%E5%8A%A1%E4%BB%A3%E7%A0%81%E6%A8%A1%E5%9E%8B.jpg)



![三层架构和DDD四层架构](https://raw.githubusercontent.com/BugCui/picBed/main/%E4%B8%89%E5%B1%82%E6%9E%B6%E6%9E%84%E5%92%8CDDD%E5%9B%9B%E5%B1%82%E6%9E%B6%E6%9E%84.jpg)

