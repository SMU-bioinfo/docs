# R_environment

​         在R语言中，不管是变量，对象，或者函数，都存在于R的环境空间中。所有对象都有自己的作用域。	

​        以R包 [nCov2019](https://github.com/GuangchuangYu/nCov2019)为例，我们在`R\dashboard.R`文件中给一个对象`shijie`赋值，希望在`inst\shinyapps\e`中的shiny app中去调用。然而遗憾的是我们在`R\dashboard.R`中建立的对象是无法直接被inst文件夹中的shiny app访问到的。这便是作用域的问题。此时我们可以先在`R\dashboard.R`中对`shijie`赋值，并在`.GlobalEnv`里创建一个新环境, 把`shijie`放里面。

```r
# R\dashboard.R
shijie <- readRDS(rds)
pos <- 1
envir <- as.environment(pos)
if (!exists("nCov2019Env", envir = .GlobalEnv)) {
    assign("nCov2019Env", new.env(), envir = envir)
}
nCov2019Env <- get("nCov2019Env", envir = .GlobalEnv)
assign("shijie", shijie, envir = nCov2019Env)
```

​       然后在inst文件夹中的shiny app中，我们从`.GlobalEnv`里找到之前创建的环境，这样就可以从此环境中提取出`shijie`这个对象了。

```r
# inst\shinyapps\e\global.R
get_city_map <- function() {
    if (!exists("nCov2019Env", envir = .GlobalEnv)) return(NULL)
    nCov2019Env <- get("nCov2019Env", envir = .GlobalEnv)
    get("shijie", envir = nCov2019Env)
}

# inst\shinyapps\e\server.R
shijie <- get_city_map()

```

代码解读：

```r
pos <- 1
envir <- as.environment(pos)
```

`as.environment()`可以获取数字或者字符串对应的环境。我们首先看一下我的R中的环境：

```r
search()
 [1] ".GlobalEnv"         "package:data.table" "package:grid"       "package:gtable"     "package:ReadAxfBOM" "package:ggplot2"    "package:stats"      "package:graphics"  
 [9] "package:grDevices"  "package:utils"      "package:datasets"   "package:methods"    "Autoloads"          "package:base"      

```

as.environment(1) 就是`.GlobalEnv`(全局环境)

```r
> as.environment(1)
<environment: R_GlobalEnv>
```

接着我们使用`assign()`函数在envir（.GlobalEnv）中新建一个环境（`new.env()`），并赋给`nCov2019Env`。

`assign()`函数的第一个参数是对象名称，第二个参数是对象取值，envir参数是某特定环境的名称。

```r
 assign("nCov2019Env", new.env(), envir = envir)
```

新环境创建出来后，我们就可以把`shijie`对象存到里面去了。

```r
assign("shijie", shijie, envir = nCov2019Env)
```

下一步就是在shiny app中把`shijie`再提取出来。

```r
nCov2019Env <- get("nCov2019Env", envir = .GlobalEnv)
get("shijie", envir = nCov2019Env)
```

与`assign()`类似，`get()`第一个参数为对象名称，envit参数为某特定环境的名称。它用来取出指定环境空间中的对象。以上两步我们便可以把`shijie`提取出来了。
