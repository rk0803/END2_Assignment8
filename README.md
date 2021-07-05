# Assignment8
First two repositories ( i.e. 2 and 3)could be suucessfully refactored with new data processing pipeline.</br>
Repo 4 was tried. The last part where inference and bleu score is displayed that could not be completed by this time. However, the model could be successfully trained. That partial part is uploaded as **partof4.....ipynb** notebook. </br>
**code_4Packed Padded Sequences, Masking, Inference and BLEU** Now contains complete work of repo 4 refactored with new data pre-processing pipeline, with attention plotted and bleu_score calculated. However, here even though the sentences generated are same, bleu_score is coming out to be zero. Which needs to be further investigated.</br>

### Finally mamanged to sort out the bleu_score.###
I needed to make the second parameter iterable of iterables, which I was not doing. Here is the code. You can ignore it,if you want, as its beyond the deadline.
__________________________________________________________________________________________
def new_calculate_bleu(model, device, max_len = 50):</br>
  > test_iter = Multi30k(split='test', language_pair=(SRC_LANGUAGE, TGT_LANGUAGE))</br>
  > trgs=[]</br>
  > predicted_trgs=[]</br>
  > for sentence in test_iter:</br>  
  >> src,trg = sentence</br>
  >> trg=tokenizer(trg)
  >> pred_trg, _ = new_translation(sentence, model, device, max_len)</br>
  >> pred_trg = pred_trg[:-1]</br>
  >> predicted_trgs.append(pred_trg)</br>
  >> trgs.append([trg])   </br>
  >> 
 return bleu_score(predicted_trgs,trgs)
__________________________________________________________________________________________ 
bscore = new_calculate_bleu(model, device)
print(f'BLEU score = {bscore*100:.2f}
 
 BLEU score = 20.70

### Team Members
Ritambhra Korpal
Pralay Ramteke
Chaitanya Vanapamala
Pallavi
