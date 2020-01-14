```
//-------------------------
//用于返回一个map,并将key设置为callId,以方便查询,避免查询时遍历
@MapKey("callId")﻿​ 


//---------------
//Example 功能强大
Example example = new Example(CandidateBrandEntity.class); //指定返回的类

example
        .selectProperties("cabId","cabName") //用于指定查询列,类内其他列会被置null
        .and().andEqualTo("cabDeleted",0) //等于
        .andLike("cabName","%d%"); //like
        .setDistinct(true); //去重
        .orderBy("cabId").desc(); //排序
//执行
List<CandidateBrandEntity> brands = brandEntityMapper.selectByExample(example);

//--------------------
//Example.Criteria(用于构建查询语句),可以创建多个Criteria,分层构建,实现where内的括号逻辑
//默认只执行第一个create的criteria,后面要and或or,上去
//select * from Brand  where (count=0,name like "%d%")or(name = "h",age = 12)
Example example = new Example(CandidateBrandEntity.class)
Example.Criteria criteria = exmaple.createCriteria();
criteria.andEqualTo("count", 0)
        .andLike("name", "%d%");

Example.Criteria criteria2 = exmaple.createCriteria()
        .andEqualTo("name,"h")
        .andEqualTo("age",12)

criteria.or(criteria2)
List<CandidateBrandEntity> brands = brandEntityMapper.selectByExample(example);
//-------------------------
```