# 1024homework
搜索输入框 

```
<!doctype html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport"
          content="width=device-width, user-scalable=no, initial-scale=1.0, maximum-scale=1.0, minimum-scale=1.0">
    <meta http-equiv="X-UA-Compatible" content="ie=edge">
    <title>Document</title>
    <link rel="stylesheet" href="search.css">
    <script src="node_modules/vue/dist/vue.js"></script>
</head>
<body>
<div id="app">
    <!--搜索框-->
    <div id="search_header">
        <img :src="search_src" alt="" id="magnifier">
        <input type="text" id="search_input" v-model="searchStr" :placeholder="place">
    </div>
    <div id="search_content">
        <div id="search_left" v-for="value in searchFor(articles,searchStr)">
            <img :src="value.image" alt="">
            <a :href="value.url">
                <p ref="value_title" :title="value.title">{{value.title}}</p>
            </a>
            <div class="hengxian"></div>
        </div>
    </div>
</div>
<script>
    new Vue({
        el: '#app',
        data() {
            return {
                search_src: 'img/放大镜.png',
                place: 'Enter your search terms',
                searchStr: "",
                articles: [{
                    "title": "What You Need To Know About CSS Variables",
                    "url": "http://tutorialzine.com/2016/03/what-you-need-to-know-about-css-variables/",
                    "image": 'https://tutorialzine.com/media/2016/03/css-variables.jpg'
                },
                    {
                        "title": "Freebie: 4 Great Looking Pricing Tables",
                        "url": "http://tutorialzine.com/2016/02/freebie-4-great-looking-pricing-tables/",
                        "image": 'https://tutorialzine.com/media/2016/02/great-looking-pricing-tables.jpg'
                    },
                    {
                        "title": "20 Interesting JavaScript and CSS Libraries for February 2016",
                        "url": "http://tutorialzine.com/2016/02/20-interesting-javascript-and-css-libraries-for-february-2016/",
                        "image": 'https://tutorialzine.com/media/2016/02/interesting-resources-february.jpg'
                    },
                    {
                        "title": "Quick Tip: The Easiest Way To Make Responsive Headers",
                        "url": "http://tutorialzine.com/2016/02/quick-tip-easiest-way-to-make-responsive-headers/",
                        "image": 'https://tutorialzine.com/media/2016/02/quick-tip-responsive-headers.png'
                    },
                    {
                        "title": "Learn SQL In 20 Minutes",
                        "url": "http://tutorialzine.com/2016/01/learn-sql-in-20-minutes/",
                        "image": 'https://tutorialzine.com/media/2016/01/learn-sql-20-minutes.png'
                    },
                    {
                        "title": "Creating Your First Desktop App With HTML, JS and Electron",
                        "url": "http://tutorialzine.com/2015/12/creating-your-first-desktop-app-with-html-js-and-electron/",
                        "image": 'https://tutorialzine.com/media/2015/12/creating-your-first-desktop-app-with-electron.png'
                    }]

            }
        },
        methods: {
            //通过函数传参的形式将需要的Value 传进来
            searchFor(value, searchStr) {
                var result = [];  //用result来存放查到的结果
                //判断不是我们需要的值就返回
                if (!searchStr) {
                    return value;
                }
                //把查询的内容转为小写的
                searchStr = searchStr.trim().toLowerCase();
                //这里value是个数组,他也有filter方法的.item是value里面的。
                result = value.filter(function (item) {
                    //判断数组中是否存在该值,存在则返回
                    if (item.title.toLowerCase().indexOf(searchStr) != -1) {
                        return item;
                    }
                });
                //将结果数组返回给v-for
                return result;
            }
        }

    })
</script>
</body>
</html>
```

***

