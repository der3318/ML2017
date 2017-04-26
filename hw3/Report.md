## �����ǲߧ@�~�T ���i
#### �Ǹ� - B03902015 / �t�� - ��u�T / �m�W - ²޳�w
#### 1. �л����A��@���uCNN model�v�A��ҫ��[�c�B�V�m�L�{�M�ǽT�v����
##### �ҫ��[�c
* Input Layer - `shape = (1, 48, 48)`
* Convlution2D - `n_filters = 64, kernal_size = (3, 3)`
* Activation - `'relu'`
* Convlution2D - `n_filters = 64, kernal_size = (3, 3)`
* Activation - `'relu'`
* MaxPooling2D - `pool_size = (2, 2)`
* Dropout - `rate = 0.25`
* Convlution2D - `n_filters = 64, kernal_size = (3, 3)`
* Activation - `'relu'`
* MaxPooling2D - `pool_size = (2, 2)`
* Dropout - `rate = 0.25`
* Flatten
* Dense - `units = 512`
* Activation - `'relu'`
* Dropout - `rate = 0.48`
* Dense - `units = 256`
* Activation - `'sigmoid'`
* Dropout - `rate = 0.48`
* Dense - `units = 7`
* Activation - `'softmax'`


##### �Ѽƶq
$(1\times64\times3\times3+64)+(64\times64\times3\times3+64)+(64\times64\times3\times3+64)$
$+(10\times10\times64\times512+512)+(512\times256+256)+(256\times7+7)\approx3,480000$


##### �V�m�L�{
* �l����ƥH`'categorical_crossentropy'`�p��
* �u�ƾ��ϥ�`'adadelta'`
* Epoch�Ƴ]��$25$
* Batch�j�p�]��$128$
* �|��V�m�Ϊ��Ϥ����k½��A�H�W�[�V�m�Ϥ����ƶq


##### �ǽT�v�ܤƹ�
![Imgur](http://i.imgur.com/BZM1naR.png)


#### 2. �ӤW�D�A�ХλP�W�z�uCNN�v���񪺰Ѽƶq�A�갵²�檺�uDNN model�v�C��ҫ��[�c�B�V�m�L�{�M�ǽT�v����H�ջP�W�D���G������A�û����A�[���F����H
##### �ҫ��[�c
* Input Layer - `shape = (2304)`
* Dense - `units = 1024`
* Activation - `'relu'`
* Dropout - `rate = 0.25`
* Dense - `units = 512`
* Activation - `'relu'`
* Dropout - `rate = 0.25`
* Dense - `units = 512`
* Activation - `'relu'`
* Dropout - `rate = 0.25`
* Dense - `units = 7`
* Activation - `'softmax'`


##### �Ѽƶq
$(2304\times1024+1024)+(1024\times512+512)+(512\times512+512)+(512\times7+7)$
$\approx3100000$


##### �V�m�L�{
* �l����ƥH`'categorical_crossentropy'`�p��
* �u�ƾ��ϥ�`'adadelta'`
* Epoch�Ƴ]��$25$
* Batch�j�p�]��$128$
* �|��V�m�Ϊ��Ϥ����k½��A�H�W�[�V�m�Ϥ����ƶq


##### �ǽT�v�ܤ�
![Imgur](http://i.imgur.com/Om8Kb4Q.png)


##### �P�uCNN�v�����
* �Ѽƶq����ɡA�uCNN�v���ĪG�|��uDNN�v�n
* �N���c�W�ӻ��A�uCNN�v�h�F�uConvolution�v�M�uPooling�v�o��Ӿާ@�A��v���ӻ��A��঳�ħ�X�Ϥ����S�x
* �uConvolution�v�M�uPooling�v�ۭ���۾F�������������Y�A�Ӥ��O��Ϥ�������C�ӹ����@���P���A���~�A�]�����C���ת��ĪG�A��٤U�Ӫ��ѼƥΦb��L���a��A�H�W�[�V�m���ǽT��


#### 3. �[������Ϥ����A���ǡuclass�v�������e���βV�H(ø�X�uconfusion matrix�v���R)
##### Confusion Matrix
![Imgur](http://i.imgur.com/t9Mlvz4.png)


##### ���R
* $\text{class}3$���Ϥ�����e���Q�Ϥ��X�ӡA�ڻ{���o�O�]�������˥��Ƹ��h�A�ǲߪ����|����h
* $\text{class}2$�M$\text{class}4$�O����e���V�c���A�b�V�m�ɼҫ��N�S��k�Ϥ��o�ܲM���A���諸���v�Ʀܥu���������k
* �q�H�����רӷQ�A$\text{class}2$�M$\text{class}4$���O�O���ߩM���L�A�o��ӱ�����{���ۦ��׭쥻�N����


#### 4. �q1�B2�D�i�H�o�{�A�ϥΡuCNN�v���T���Ǧn�B�A��ø�X��usaliency maps�v�A�[��ҫ��b���uclassification�v�ɡA�O�ufocus�v�b�Ϥ������ǳ����H
| Origin Image | Saliency Map | Masked Image |
|:-:|:-:|:-:|
|![Imgur](http://i.imgur.com/PLjbhKB.png)|![Imgur](http://i.imgur.com/vMj3LVL.png)|![Imgur](http://i.imgur.com/FVXI0ZM.png)|


#### 5. ��1�B2�D�A�Q�ΤW�ҩҴ��쪺�ugradient ascent�v��k�A�[��S�w�h���ufilter�v�̮e���Q���عϤ��uactivate�v
* �ġu�@�v�h�uCNN�v��$32$��filter�A���O���Q�H�U�Ϥ��E��
![Imgur](http://i.imgur.com/JiQCWTU.png)
* �i�H�o�{�j�������Ϥ����٬O�uWhiteNoise�v�A�����i�઺��]�O - �ؼШ�ƬO$a^k=\sum_{i=1}^{46}\sum_{j=1}^{46}a^k_{ij}$�A�C�ӹ�����ؼШ�ƪ��^�m���O�ۦP���]���|�Qfilter���C�@�歼��@���^�|�Ҩӻ��A�Yfilter�O$[1,2,3;4,5,6;7,8,9]$�A����@��pixel�W�[$1$�A�ؼШ�Ƴ��|�W��$1+2+...+9=45$


#### 6. �q�utraining data�v�����������ulabel�v�A��@�usemi-supervised learning�v
##### ��@�覡
1. �N��ƨ�$4:1:1$�����utraining/unlabel/validation data�v
2. ���b�ulabeled training data�v�V�m$40$��epoch
3. ��uunlabel data�v�i��@���w��
4. �o�ɭԡA�C�@�i���аO�Ϥ������H�U����T�G�u�U��class�����v�v�H�Ρu���v�̤j��class�v
5. �Y�Y�@�i���аO�Ϥ��A��u���v�̤j��class�����v�ȡv�j��$0.9$�A�N�N���[�J�V�m��ƶ��A�b�U�@���q�ϥΡA�Ϥ��h���L
6. �b�ulabeled data�v�M�upseudo labeled data�v�զ����V�m��ƶ��W�A�A�V�m$10$��epoch
7. �A�i��@���w���A�ç⵲�G�����̲ת���X


##### �ǽT�v�����
* �Lsemi-supervised�B$40$��epoch - `Validation Acc = 0.6443`
* �Lsemi-supervised�B$50$��epoch - `Validation Acc = 0.6518`
* ��semi-supervised�B$50$��epoch - `Validation Acc = 0.6602`


#### 7. �b�uProblem 5�v���A���ѤF3�ӡuhint�v�A�i�H���չ�@���[��
* �H�U�O�ġu�@�v�h�uCNN�v���A$64$��filter����X
![Imgur](http://i.imgur.com/CMrbNWM.png)
* �[���i�H�o�{�A�����hfilter�����G�O�X�G�ۦP���A�ڻ{���o�i���ܸӼh��filter�ƥب�ꤣ�ݭn�o��h�]�èS���s����T�Qfilter��X�ӡ^
* ���~�A�]�i�H�o�{�A�ѩ�o�O�Ĥ@�h�uCNN�v�A�j�������ϧΩM�쥻���Ϥ����ܬ۪�
