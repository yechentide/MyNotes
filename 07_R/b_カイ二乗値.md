# カイ二乗値



### カイ二乗値

![image-20201011083003194](/Users/yechentide/Documents/My Notes/07_R/b_カイ二乗値.assets/image01.png)

![image-20201011083028509](/Users/yechentide/Documents/My Notes/07_R/b_カイ二乗値.assets/image02.png)

![image-20201011083047388](/Users/yechentide/Documents/My Notes/07_R/b_カイ二乗値.assets/image03.png)

![image-20201011083109288](/Users/yechentide/Documents/My Notes/07_R/b_カイ二乗値.assets/image04.png)

### 結論

P値が0.05未満であったことから，==クロス表の行と列は独立でない(統計的に有意な関連がある)==と主張することができる

- P値を有意確率，カイ二乗値を検定統計量という。

```R
data <- read.csv("font.csv", header=TRUE, row.names=1)
F <- table(data)
chisq.test(F)
```

