# FastJson
- 阿里出品的Json库，和名字一样快速
- FastJson 在进行操作时，是根据 getter 和 setter 的方法进行的
- 参考:https://www.w3cschool.cn/fastjson/fastjson-api.html

# 序列化
- JSON.toJSONString(obj) 将object转为字符串
- JSON.toJSONBytes(obj) 将object转为utf8 bytes字节组
- JSON.writeJSONString(output,obj) 将obj转为字符串并写入到output中，output支持Write/OutPutStream

# 反序列化
- JSON.parseObject(jsonStr,obj.class) 字符串反序列化为指定calass
- JSON.paresObject(jsonStr, TypeReference<T> type) 反序列化为泛型类型的JavaBean
- JSON.parseObject(String text) 反序列化为JSONObject

# JSONArray
- 可以当List用，但这个List里存的是Object,foreach时，需要转一下
- JSONArray.getJSONObject(index) 根据下标获取JSONObject,返回是JSONObject
- JSONArray.parseArray(str) 将字符串转换为JSONArray

# JSONObject
- 可以理解为JSON的map,可以直接像map一样get