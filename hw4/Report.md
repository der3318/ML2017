## �����ǲߧ@�~�| ���i
| �Ǹ� | �t�� | �m�W |
|:-:|:-:|:-:|
| B03902015 | ��u�T | ²޳�w |
#### 1.1. �uDataset�v���e$10$�ӤH���e$10$�i�Ӥ��������y�M�uPCA�v�o�쪺�e$9$�ӡueigenfaces�v
| Average | Eigenfaces |
|:-:|:-:|
| ![Imgur](http://i.imgur.com/LmEeoCO.png) | ![Imgur](http://i.imgur.com/9q3vKBv.png) |


#### 1.2. �uDataset�v���e$10$�ӤH���e$10$�i�Ӥ�����l�Ϥ��M�ureconstruct�v��(�Ϋe$5$�ӡueigenfaces�v)
| Origin | Reconstruction |
|:-:|:-:|
| ![Imgur](http://i.imgur.com/aKszI32.png) | ![Imgur](http://i.imgur.com/QzcU0y9.png) |


#### 1.3. �uDataset�v���e$10$�ӤH���e$10$�i�Ӥ���v��utop k eigenfaces�v�ɴN�i�H�F��$<1\%$���ureconstruction error�v
$k=59$, RMSE$=2.55186750057$


#### 2.1. �ϥΡuword2vec toolkit�v���U�ӰѼƪ��ȻP��N�q
* `size=50` <int> - ���V�q������
* `window=5` <int> - �Ҽ{����h�֭ӵ��y
* `hs=1` <int> - �O�_�ϥΡuHierarchical Softmax�v���u��
* `negative=0` <int> - �O�_�ϥΡunegative sampling�v���u��
* `threads=1` <int> - �V�m�ɨϥΪ�������ƶq
* `min_count=5` <int> - �X�{�h�֦��H�U�]���t�^�����J�N�ٲ�
* `alpha=0.025` <float> - �N�O�ulearning rate�v
* `cbow=1` <int> - �ϥΡucbow(0)�v�٬O�uskip-gram(1)�v�ҫ�


#### 2.2. �N�uword2vec�v�����G��v��$2$������
![Imgur](http://i.imgur.com/YadRlXv.png)


#### 2.3. �q�W�D��ı�ƪ��Ϥ��[���F����
* �Ѥ�����W�r���uembedding�v�����۪�(���k�U�������@�s)
* �]�k�ǰ|�������A�p�ustudents�v�B�uwizards�v�B�uschool�v�����J�]���۪񪺡urepresentation�v
* �Y�B�y���B���x�h�O�t�@�s�A���O�uhair�v�B�ueyes�v�B�umouth�v�M�uhead�v
* �W�����uwispered�v�M�uprofessor�v�Pı�@�I���Y���S���A�y�Ыo�ܱ���A�q���n�q��L���פ~��ݥX���̪��t�O


#### 3.1. �иԥ[�����A���p��l���ת���z�B�X�z�ʡA�o��k���q�Ωʦp��
* ��z
    1. ��C�ӭ�l����$d_i$�A��`gen.py`���O����$200$���u$N=400$�B$d_h=\text{randint}(60,80)$�v���usample dataset�v
    2. ���ɡA�C�ӡusample dataset ($d_i$,$t$)�v����$400$��$\mathbb{R}^{100}$���V�q�A$40000$�ӼƭȡA�w�q$var(d_i,t)$���o�|�U�ӼƭȪ��ܲ��ơA�䤤$d_i\in\{1,2,...,60\}$�B$t\in\{1,2,...,200\}$
    3. ���C��$d_i$�A�p��$var(d_i)=\frac{\sum_{t=1}^{200}var(d_i,t)}{200}$�A�i�H�o��U�������Y�� ![Imgur](http://i.imgur.com/nWhH1t0.png)
    4. �ڭ̥i�H�o�{�A�H�ۭ�l���״����A�udataset�v���Ҧ��ƭȤ��ܲ��ƪ�����ȷ|��ۤW��
    5. ����A���w�@�ӥ�����l���ת��udataset�v�A�ڭ̥u�n���o�ӡudataset�v�����Ҧ��ƭȭp���ܲ��ơA�ç�X�̱���o�ӼƭȪ�$var(d_i)$�A�N�q��$d_i$�O�o�Ӹ�ƶ�����l����
    6. �b�ukaggle public�v����{ - `MAE=0.11561`
* �X�z��
    * ²��ӻ��A�N�O�ϥ�`gen.py`���ͳ\�h����ƶ��A�ðO����l���פW�ɹ��ƶ��ܲ��ƪ��v�T
    * ��l���׶V���A��X�V�q���ƭȭ̥��ӴN�V�e�����[�A�P�[��۲�
* �q�Ω�
    * �򥻤W���O�ܹ��
    * ���D���D�p��q��l���ײ��͸�ƥH�θ�Ʀb��l�V�q�Ŷ��������A���M�S��k�j�q���͡usample dataset�v�ӭp��Y�Ӻ��ת��ܲ��ƴ����


#### 3.2. �N�A����k���b�uhand rotation sequence datatset�v�W�o�줰�򵲪G�H�X�z�ܡH
* �o�쪺���G
    * �uhand rotation sequence dataset�v���@��$481$�i$480\times512$���ۤ��A�Y$481$��$245760$�����V�q�A�@$118210560$�Ӽƭ�
    * �o�ǼƭȪ��ܲ��Ƭ���$944.391$�A�̾a��o�ӼƭȪ�$var(d_i)$�O$990.0857$ (��$d_i=33$)
    * �]���A�q���o�Ӹ�ƶ�����l���׬�$33$
* �ڻ{�����X�z�A�]���o�ǹϤ����㤣�O�ѫe�@�D���覡���ͪ��A�[��쪺���פ]���P�A�ҥH��ƶ��u��l���׻P�ܲ��ơv�����Y���ӷ|���ܡA���ઽ�����Өϥ�


