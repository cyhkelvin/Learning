# 經驗法則 (empirical law)
  - 單峰對稱或鐘形分配時，估計涵蓋的機率或個數: 68% - 95% - 99.7%
# 柴比雪夫不等式 (chebyshev's inequality)
  - P(|X-mu|<=k*sigma)>=1-1/k^2, k>1
  - k 個標準差內估計涵蓋的數量
# 證明柴比雪夫 (詳略)
  - f(x): probability density function; pdf
  - sigma^2 = integrate(X from  -inf to inf, ((X-mu)^2)*f(X))
  -->拆項後配合 X <= mu-k*sigma and X >= mu+k*sigma 證明，詳略。
# 馬可夫不等式 (markov inequality)
  - P(X>=k) <= E(X)/k
  - 證明: 
     (1) 建立 indicator function: I(x)=1 if x>=k else 0
     (2) I(x) <= x/k
     (3) P(x>=k) = integrate(X from k to inf, f(x))
                 = integrate(X from -inf to inf, I(x)f(x)) = E(x) <= E(x/k) = E(x)/k 得證
# 柴比雪夫單邊
  - P(x>=k)<= sigma^2/(sigma^2+k^2) 證略
         
         
