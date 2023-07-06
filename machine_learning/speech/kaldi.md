# kaldi

## kaldi tools
  1. wav-reverberate: 
    egs/wsj/s5/steps/data/reverberate_data_dir.py
    egs/aspire/s5/local/nnet3/run_ivector_common.sh
  2. introduction of parameters in training process:
    https://arxiv.org/pdf/1410.7455.pdf
  3. model edit-config: src/nnet3/nnet-utils.h
  4. chunk, egs, minibatch: 
    https://www.cnblogs.com/JarvanWang/p/10145897.html
  5. documents/ark files viewing:
    https://www.cnblogs.com/sunhongwen/p/9417592.html
  6. lattice:
        查看lattice: http://jrmeyer.github.io/asr/2016/12/15/Visualize-lattice-kaldi.html
    lattice to text:../../../src/latbin/lattice-copy
    (lattice content: https://senarvi.github.io/kaldi-lattices/)
    sudo apt-get install graphviz-->./utils/show_lattice.sh
    lattices number sequence:
    (1)even-->divide by 2, equal line-index in final.mdl, represent state 0 of pdf at that line
    (2)odd-->same pdf of previous even number but for state 1(which means the self loop state)
    -->change state at every even numbers.(so only even number would be adjacent.) Numbers for SIL equals to numbers of SIL states in topo. To Sum up, kaldi check index of each pdf state in model file but not actually pdf-id and determine if state changing by even or odd number(state-change means not continuous on same tree leave).
  7. observe learning curve:
    steps/nnet3/report/generate_plot.py (install pdflatex)
  8. draw-tree install graphiz, dot and remember to replace ":", "<", ... (some punctuation that dot didn't support.)
  9. lattice-1best --lm-scale=\$lmwt --word-ins-penalty=\$wip

## next generation kaldi
  1. **lhotse** training prepare for acoustic data [github](https://github.com/lhotse-speech/lhotse), [doc](https://lhotse.readthedocs.io/en/latest/getting-started.html)
  2. **k2** kernel training steps and utils [github](https://github.com/k2-fsa/k2), [doc](https://k2.readthedocs.io/en/latest/index.html), [google colab](https://colab.research.google.com/drive/1qbHUhNZUX7AYEpqnZyf29Lrz2IPHBGlX?usp=sharing)
  3. **icefall** example scripts [未完成，目前命名 snowfall 放在 k2 github 下]
