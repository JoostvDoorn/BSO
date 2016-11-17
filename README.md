Code for [Sequence-to-Sequence Learning as Beam-Search Optimization](http://aclweb.org/anthology/D/D16/D16-1137.pdf) (Wiseman and Rush, 2016).

This code is adapted from a much earlier version of Yoon Kim's [seq2seq-attn code](https://github.com/harvardnlp/seq2seq-attn).

An actual README with detailed instructions for running experiments coming soon!


MIT License.


# Instructions
Download the German->English data
```
./prepareData.sh
```
Preprocess dataset using https://github.com/harvardnlp/seq2seq-attn
```
python preprocess.py --targetvocabsize 30000 --srcvocabsize 30000 \
--srcfile data/train.de-en.de \
--targetfile data/train.de-en.en \
--srcvalfile data/valid.de-en.de \
--targetvalfile data/valid.de-en.en \
--outputfile data/bso \
```
Pretrain the model
```
th pretrain.lua -data_file data/bso-train.hdf5 -val_data_file data/bso-val.hdf5 -gpuid 1
```
