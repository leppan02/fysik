```python
from statistics import *
import math
```


```python
f_1 = lambda s, sp: 1/(1/s+1/sp) 
# sp*d(f)/d(sp)+s*d(f)/d(s) propagation of error
error_f_1 = lambda s, sp: s*(sp/(sp+s))**2+sp*(s/(sp+s))**2
```

# 1a


```python
val = [[ 97 ,602],[ 98 ,600],[ 97 ,601],[ 98 ,609],[ 95 ,600],
       [ 95 ,599],[ 96 ,601],[ 93 ,598],[100 ,599],[ 97 ,599],
       [ 95 ,594],[ 96 ,597],[ 94 ,597],[ 97 ,600],[100, 604]]
s = [i[0] for i in val]
sprime = [i[1] for i in val]

```


```python
average = (mean(s) , mean(sprime))
sdev = (stdev(s), stdev(sprime))
sdev2 = (stdev(s)/math.sqrt(14), stdev(sprime)/math.sqrt(14))
```


```python
focal=f_1(average[0],average[1])
deltaf = error_f_1(sdev2[0],sdev2[1])
print("focal", focal)
print("relative error", deltaf/focal)

```

# 1b


```python
val = [[108, 384, 1], [105, 388, 1], [105, 385, 1], [102, 439, 2],
       [106, 443, 2], [101, 446, 2], [105, 498, 3], [102, 494, 3],
       [98, 492, 3], [97, 544, 4], [96, 544, 4], [100, 545, 4],
       [95, 598, 5], [97, 599, 5], [93, 602, 5], [95, 655, 6],
       [96, 654, 6], [96, 654, 6], [97, 698, 7], [95, 702, 7],
       [95, 700, 7], [93, 756, 8], [95, 752, 8], [93, 750, 8],
       [93, 799, 9], [95, 804, 9], [93, 801, 9], [94, 851, 10],
       [93, 852, 10], [92, 850, 10]]
s = [i[0] for i in val]
sprime = [i[1] for i in val]
```


```python
focals = [f_1(s[i],sprime[i]) for i in range(30)]
```


```python
error = stdev(focals)/math.sqrt(29)
print("average focal point over all groups", mean(focals))
print("approximate relative error", error/mean(focals))
```

# 2



```python
f_2 = lambda sp, M: sp/(M+1)
error_f_2 = lambda sp, M: sp/(M+1)+M*sp/((M+1)**2)
#sp*d(f)/d(sp)+M*d(f)/d(M) propagation of error
```


```python
val = [[ 897,  9.8, 1],[ 901,  9.6, 1],[ 904,  9.6, 1],
       [1150, 12.5, 2],[1150, 12.8, 2],[1153, 12.7, 2],
       [1406, 15.5, 3],[1406, 15.6, 3],[1412, 15.6, 3],
       [1662, 18.4, 4],[1650, 18.4, 4],[1655, 18.6, 4],
       [1904, 21.3, 5],[1908, 21.4, 5],[1909, 21.3, 5]]
sprime = [i[0] for i in val]
magnitude = [i[1] for i in val]
```


```python
focals = [f_2(sprime[i],magnitude[i]) for i in range(15)]
```


```python
error = stdev(focals)/math.sqrt(14)
print("average focal point over all groups", mean(focals))
print("approximate relative error", error/mean(focals))
```

    average focal point over all groups 84.82095851658782
    approximate relative error 0.0024328809676399748


# 3
we can calculate  where the picture converges after passing through the first lens, calculate what the focal point of the negative ray must be for the ray to converge on the back plane. 

```python
distance_to_middle_picture = 1/(1/8.48172-1/11)
#1/middle_picture=1/s+1/sp>1/sp=1/f-1/s
```


```python
from IPython.display import Image
from IPython.core.display import HTML 
Image(url= "https://cdn.discordapp.com/attachments/385089923176202241/785155551570165781/unknown.png")
```




<img src="https://cdn.discordapp.com/attachments/385089923176202241/785155551570165781/unknown.png"/>


