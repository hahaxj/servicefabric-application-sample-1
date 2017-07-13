# servicefabric-application-sample-1

实现抓取新闻数据，并去除html标签，之后处理分词，统计词的出现频数，提供WEB API可以查询词频！

**建议做法：**
1. 实现两个Reliable Actors 服务  
   一个负责抓取  
   一个负责处理并存储到Storage，之后将地址信息加入到Storage Queue中  
2. 实现两个Reliable Services  
   一个实现订阅Queue中消息，实现读取文章，中文分词，并调用存储服务    
   一个实现存储词的频数（建议固定分区书，使用Hash定位分区， hash（词）/ 分区数）  
3. 实现Reliable Stateless Service 提供WEBAPI查询词频   
