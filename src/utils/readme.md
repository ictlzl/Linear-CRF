1.将训练语料转换成crf++需要的格式

python make_crf_train_data.py pku_train.utf8 pku_training_out.utf8 

2. 使用训练，得到model 文件

crf_learn tmpl.txt pku_training_out.utf8 pku.model

3. 将测试语料转换成crf++需要的格式

python make_crf_test_data.py pku_test.utf8 pku_test_out.utf8

4. 得到标注文件，还要用脚本进行转换，略繁琐（可以跳过直接进入下一步 ）

crf_test -m pku.model pku_test_out.utf8 > pku_test_result.utf8 

5. 执行得到分词输出结果

 python crf_segmenter.py pku.model pku_test.utf8 pku_test_word.utf8 

6.对分词结果进行评测

crf_tag_score.py pku_test_gold.utf8 pku_test_word.utf8

