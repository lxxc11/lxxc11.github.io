# ElasticSearch  
 1.[ES如何添加字段](#ES如何添加字段)  
 2.[ES如何编辑数据](#ES如何编辑数据)   
 3.[ES如何删除数据](#ES如何删除数据)   
 4.[ES使用脚本编辑数据](#ES使用脚本编辑数据)
 
 ## ES如何添加字段  
``` 
PUT dm_cloudlocation_all_XX/_mapping/index
{
  "properties": {
    "traffic_map": {
      "type": "keyword"
    },
    "cert_date": {
      "type": "date",
      "format": "yyyy-MM-dd HH:mm:ss"
    },
    "other_name_text": {
      "type": "nested",
      "properties": {
        "name": {
          "type": "text",
          "analyzer": "ik_max_word"
        }
      }
    }
  }
}
```
## ES如何编辑数据  
```
POST dm_cloudlocation_all_XX/index/6e27fc7e69a087706d1dbb1c155c87d7/_update
{
  "doc": {
    "is_cert": "1",
    "enterp_capital": [
      {
        "num": 4,
        "label": "1亿及以上"
      },
      {
        "num": 5,
        "label": "5000万-1亿"
      }
    ],
    "park_id": "a41e20a012bbb4b12e318acb917215d2"
  }
}
```
## ES如何删除数据   
``` 第一种
DELETE  dm_cloudlocation_all_XX/index/a48246b3d4c2fc9c9142e6b92a58f21e
```   
``` 第二种
GET dm_cloudlocation_all_XX/_delete_by_query
{
  "query": {
    "bool": {
      "must": [
        {
          "term": {
            "park_id": {
              "value": "12345678"
            }
          }
        }
      ]
    }
  }
}
```
## ES使用脚本编辑数据
```
POST dm_cloudlocation_all_XX/_update_by_query
{
  "script": {
    "source": "ctx._source['gaoxinqu']='经开区'"
  },
  "query": {
    "terms": {
      "park_id": [
        "da318967261f7294e535e6ab76086503",
        "8d552a92d061d99f765a1eb01ce1978a"
      ]
    }
  }
}
```  
