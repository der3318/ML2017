## Machine Learning Report #2
#### B03902015 ��u�T ²޳�w
#### 1. �л����A��@��generative model�A��V�m�覡�M�ǽT�v����H
* Feature�������A�u�Ҽ{�uage�v�o�@���A�õ���discreate���ƭ�
* �ؼШ�Ʃw��$\prod_{(y,x)\in D}\mathbb{P}(x,y)$�A�䤤$\mathbb{P}(x,y)=\mathbb{P}(x)\mathbb{P}(y|x)$
* ���ϥؼШ�Ƴ̤j�ơA�i�o$\mathbb{P}(y=1|x=t)=\frac{c_{t1}}{c_t}$, where $c_{t1}$ is the number of training data with $(x,y)=(t,1)$ and $c_t$ is the number of training data with $x=t$
* Accuracy on validation set: about $65.5\%$


#### 2. �л����A��@��discriminative model�A��V�m�覡�M�ǽT�v����H
* Feature�������ϥΥ���106����ơA��@logistic regression
* ���ư�feature scaling�A�Nfeature���U���ƭ��Y���$[0,1]$
* $\mathbb{P}(y=1|x)=\sigma(W\mathbb{x}+b)$, where $W\in\mathbb{R}^{2\times106}$ and $b\in\mathbb{R}^2$
* �l����Ʃw��$-\sum(y\mathbb{P}(y=1|x)+(1-y)\mathbb{P}(y=0|x))$�A�Ycorss entrophy
* �Hgradient descent��s�Ѽ�$W,b$
* Batch size�]��$10000$�A�]$1500$��epoch
* Accuracy on validation set: about $84.3\%$


#### 3. �й�@��J�S�x�зǤ�(feature normalization)�A�ðQ�ר���A���ҫ��ǽT�v���v�T�C
* Feature scaling�i�j�P�����uRescaling�v�ΡuStandardization�v�A�Ĥ@�جO�ڭ쥻���覡�A�ĤG�ثh�O���D�n�D����k�C
* Rescaling $\Rightarrow x'=\frac{x-\min(x)}{\max(x)-\min(x)}$
* Standardization $\Rightarrow x'=\frac{x-\bar x}{\sigma}$, where $\sigma$ is the standard deviation
* ��@��������G�O��̮t���h�Avalidation set���ǽT�v�����b$84\%$��


#### 4. �й�@logistic regression�����W��(regularization)�A�ðQ�ר���A���ҫ��ǽT�v���v�T�C
* ����@L$2$-norm���W�ơA�ڴ��l����ƥ[�W$\lambda h(w)$�o�@���A�Ϧ��u��Ƥ@��
* �M�Ϋ�A�btraining set�W��loss���㴣���A�B�ǽT�v�L�k���ɨ�$85\%$�H�W
* Accuracy on validation set: about $84.2\%$
* �ڻ{���ҫ���{���n��]�i��O�o�ǡG�ݭn��h��epoch�ӭ��Closs�B�쥻���ҫ������ץ��ӴN�����A�]�����W�ƮĪG����


#### 5. �аQ�קA�{������attribute�ﵲ�G�v�T�̤j
* �N�ڪ��[��A�uAge�v�i��O�@���ܭ��n������
* Generative model���A��Ҽ{�uAge�v�N�঳$65\%$�H�W���ǽT�v
* �����ե[�J�uAge������v��@�s��feature�A�bvalidation set�W����{�]���ǷL������

