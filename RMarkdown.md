# 用R Markdown创建文档


+ Blog
    - [blogdown](https://github.com/rstudio/blogdown)
+ Book
    - [bookdown](https://github.com/rstudio/bookdown)
	- [bookdown](https://bookdown.org/yihui/bookdown/)
+ CV
    - [vitae](https://github.com/ropenscilabs/vitae)
+ Document
    - [rmarkdown](https://github.com/rstudio/rmarkdown)
+ Poster
    - [posterdown](https://github.com/brentthorne/posterdown) 

# R Markdown Tutorial
+ Tutorial:<http://www.jacolienvanrij.com/Tutorials/tutorialMarkdown.html>, <https://ourcodingclub.github.io/2016/11/24/rmarkdown-1.html>

# R Markdown questions
+ <https://stackoverflow.com/questions/20303826/highlight-bash-shell-code-in-markdown>
+ <https://stackoverflow.com/questions/25104738/text-highlight-in-markdown>

# Writing Mathematic in R Markdown 
+ <http://csrgxtu.github.io/2015/03/20/Writing-Mathematic-Fomulars-in-Markdown/>
+ <https://github.com/goessner/mdmath>
 ## Example
 ```
 $$ c^2 = a^2 + b^2 $$
 ```
 > <p align="center"><img src="/tex/7588eefc6e080bcc9f4f1cab40ece714.svg?invert_in_darkmode&sanitize=true" align=middle width=86.16804239999999pt height=15.572667pt/></p>
 
 ```
 $ c = \sqrt{a^2+b^2} $
 ```
 > <img src="/tex/30fa3f17e7c323c7585f3c6445b8624b.svg?invert_in_darkmode&sanitize=true" align=middle width=93.31412144999999pt height=28.712280299999996pt/>

 ```
 $$
 M = \left(\begin{array}{ccc}
 x_{11} & x_{12} & \ldots \\
 x_{21} & x_{22} & \ldots \\
 \vdots & \vdots & \ldots \\
 \end{array}\right)
 $$
 ```
 > <p align="center"><img src="/tex/9f79bddd902248f01cd901cf899a6230.svg?invert_in_darkmode&sanitize=true" align=middle width=183.5615364pt height=69.04177335pt/></p>

 ```
 $$ h_{\theta} = \theta_{0}x + \theta_{1}x \tag{1}\label{eq:test} $$
 Referring to Eq. $\eqref{eq:test}$.
 ```
 > <p align="center"><img src="/tex/e890b93fcc606de3d83b375f1ea6f682.svg?invert_in_darkmode&sanitize=true" align=middle width=404.0818518pt height=16.438356pt/></p>
 
 Referring to Eq. <img src="/tex/4b787ab623e8628ac80a613b7a736a1c.svg?invert_in_darkmode&sanitize=true" align=middle width=30.63921959999999pt height=24.65753399999998pt/>.


