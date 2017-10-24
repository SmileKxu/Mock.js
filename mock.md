### mock 可以用来生成随机数据，拦截 Ajax 请求，然后可以根据模拟数据渲染页面。
#### 具体的作用有:
- 基于数据模板生成模拟数据
- 基于 HTML模板 生成模拟数据
- 拦截并模拟 ajax 请求

#### mock 可以随机生成文本、数字、布尔值、日期、邮箱、链接、图片、颜色等。
#### mock 可以直接引入 mock.js 在前端模拟数据，并不需要后台，demo如下:
```
<script src="http://mockjs.com/dist/mock.js"></script>
<script>
  
  // 配置模拟数据:
  Mock.mock(url,{ // 该 url 是 ajax 发送请求的url
    'name': '@name',
    'age|1-100': 100,
    'color': '@color'
 });
 
  // 发送Ajax请求:
  $.ajax({
    url: 'http://g.cn',
    dataType: 'json'
  }).done((data, status, xhr) =>{
     console.log(
     JSON.stringify(data, null, 4) 
    )
  });

</script>
```
上面代码则就会随机生成一条数据。

若要生成多条数据 如下:
```
// 引入 mock 中的 Random 模块

  let Random = Mock.Random;
  Mock.mock(url, {
  
  'tableDate|n':[{  // n 就是生成多少条数据的值
     data: ()=>Random.data(),
     name: ()=>Random.cname(),
     address: ()=>Random.county(true)
  }]  
 });
 
 // 发送 ajax 请求
 $.ajax({
    url: 'http://g.cn',
    dataType: 'json'
  }).done((data, status, xhr) =>{
     console.log(
     JSON.stringify(data, null, 4) 
    )
  });
 
  
  

```
