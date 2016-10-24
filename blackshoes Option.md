

```python
class BlackSholes:
    
    def __init__(self, S0, K, T, r, Sigma, div = 0):
        self.S0 = S0  
        self.K = K 
        self.T = T  
        self.r = r
        self.Sigma = Sigma
        self.div = div
   
    def Call_Value_CF(self):
        from math import log, sqrt, exp
        from scipy import stats
        d1 = (log(S0 / K) + (r + 0.5 * Sigma ** 2) * T) / (Sigma * sqrt(T))
        d2 = (log(S0 / K) + (r - 0.5 * Sigma ** 2) * T) / (Sigma * sqrt(T))
        C0 = (S0 * stats.norm.cdf(d1, 0, 1)) - K * exp(-r * T) * stats.norm.cdf(d2, 0, 1)
        #return C0
        ValMethod = 'CF'
        self.display(ValMethod, C0)
        
    def Put_Value_PF(self):
        from math import log, sqrt, exp
        from scipy import stats
        d1 = (log(S0 / K) + (r + 0.5 * Sigma ** 2) * T) / (Sigma * sqrt(T))
        d2 = (log(S0 / K) + (r - 0.5 * Sigma ** 2) * T) / (Sigma * sqrt(T))
        C0 =  K * exp(-r * T) * stats.norm.cdf(-d2, 0, 1)-(S0 * stats.norm.cdf(-d1, 0, 1))  
        ValMethod = 'PF'
        self.display(ValMethod, C0)
        
    # 方法：顯示計算結果
    def display(self, ValMethod, C0):
        if ValMethod == 'CF':
            print('Call (' + ValMethod + '): ' + str(C0))
        elif ValMethod == 'PF':
            print('Put (' + ValMethod + '):' +str(C0))
```


```python
S0 = 100
K = 105
T = 1
r = 0.05
Sigma = 0.2

BS = BlackSholes(S0, K, T, r, Sigma)
BS.Call_Value_CF()
BS.Put_Value_PF()

```

    Call (CF): 8.02135223514
    Put (PF):7.90044180772
    


```python

```
