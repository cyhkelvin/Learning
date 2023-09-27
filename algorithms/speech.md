# speech

## traditional speech recognition process
[wiki](https://zh.wikipedia.org/zh-tw/%E8%AF%AD%E9%9F%B3%E8%AF%86%E5%88%AB)
語音辨識（speech recognition）技術，也被稱為自動語音辨識（英語：Automatic Speech Recognition, ASR）
、電腦語音識別（英語：Computer Speech Recognition）或是語音轉文字識別（英語：Speech To Text, STT）

### acoustic feature
   - Linear Predictive Coefficient，LPC
   - Mel-Frequency Cepstral Coefficients，MFCCs
   - Perceptual Linear Predictive，PLP
   - Fbank
### acoustic model
   - tri-phone with HMM
   - GMM
   - disicion tree
   - regression methods: 
### lexicon
### language model
   - n-gram
   - preplexity estimation
   - smooth techniques: Katz, Kneser-Ney
   - search: viterbi-beam, n-best
### model loss
   - Maximum Likelihood Linear Regression
   - lattice-based MLLR
   - lattice-free MLLR  