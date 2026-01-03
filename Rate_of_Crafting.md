# Crafting
Within florr.io, crafting is the art that turns collection into control and chance into intention.

Every failed craft carries the quiet ache of wasted petals, while each success blooms with rare delight—reminding players that careful calculation is not caution, but wisdom.

~~If you got a Super Petal from 5 Ultra Petals, you are gay!!!~~

Here is the code.

```cpp
#include<bits/stdc++.h>
using namespace std;
int n,k,t;
long double p,f[5005][5005];
int main() {
	cin>>n>>k>>p>>t;
	f[0][0]=f[1][0]=f[2][0]=f[3][0]=f[4][0]=1;
	for(int i=5;i<=n;++i) {
		for(int j=0;j<=k;++j) {
			if(j==0) f[i][0]=(1-p)*0.25*(f[i-1][0]+f[i-2][0]+f[i-3][0]+f[i-4][0]);
			else f[i][j]=(1-p)*0.25*(f[i-1][j]+f[i-2][j]+f[i-3][j]+f[i-4][j])+p*f[i-5][j-1];
		}
	}
	printf("%.*Lf\n",t,f[n][k]);
	return 0;
}
```

#### Let's analyze it.

n : the number of petals to be used in crafting.

k : the expected number of petals to be crafted.

p : the success probability per crafting attempt.

t : the number of decimal places to retain in calculations.

f[i][j] : the probability of transitioning from i petals to j petals after one attempt.

## Usages

1. 40 Ultra Petals -> 1 Super Petal (p=0.01, r=4)

input :
```cpp
40 1 0.01 4
```

output :
```cpp
0.1298
```

2. 200 Mythic Petals -> 0 Ultra Petals (p=0.02, r=5)

input :
```cpp
200 1 0.02 5
```

output :
```cpp
0.20418
```

In short, it is common to get unexpected results.

So ~~use oracle~~ don't be discouraged when you failed.
