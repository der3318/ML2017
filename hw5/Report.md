## �����ǲߧ@�~�� ���i
| �Ǹ� | �t�� | �m�W |
|:-:|:-:|:-:|
| B03902015 | ��u�T | ²޳�w |
#### 1. �аݡusoftmax�v�A���A�X�@�������@�~���uoutput layer�v? �g�X�A�̫��ܪ��uoutput layer�v�û����z�ѡC
* �ҫ������c
    | Layer | Parameters |
    |:-:|:-:|
    | Embedding | `input_dim = 3000`, `output_dim = 50`, `input_length = 50` |
    | LSTM | `units = 128`, `dropout = 0.2`, `recurrent_dropout = 0.2` |
    | Dropout | `rate = 0.2` |
    | Dense | `units = 64` |
    | Dropout | `rate = 0.2` |
    | Activation | `activtion = "relu"` |
    | Dense | `units = 38`, `activation = "sigmoid"` |
* �usoftmax�v���A�X�@�������@�~���uoutput layer�v
* �ڿ�ܡusigmoid�v�@���̫�@�h���uactivation function�v�A��]�p�U
    * �ڧƱ�uoutput layer�v��$38$�ӡuunit�v�A���O�N��Ӥ峹�P�U�ӡutag�v�������{��
    * �ϥΡusigmoid�v���ܡA�۷��Τ@�ӡu$0-1$�v�������ƭȨӴy�z�������{�סA�u$1$�v��ܫD�`�����A�Ϥ��u$0$�v��ܵL���C�@�g�峹�i��M�h�ӡutag�v�����A�Y�umulti-label�v�A�]���uoutput layer�v���i�঳�h�Ӥj��u$0.5$�v���ƭ�
    * �p�G�ϥΡusoftmax�v�A$38$�ӼƭȪ��`�M�|����@�A�B�C�@�Ӽƭȳ������t�A���O�N��Ӥ峹�����U�ӡutag�v�����v�A�䤤�@�ӡutag�v���v���A�N��ܨ�L�utag�v���v�������C�C�o�ؿE����ơA����A�X�uone-label�v����ơA�Y�U�ӡutag�v�����������A�C����ƥu�|�M�䤤�@�ӡutag�v����


#### 2. �г]�p�������ҤW�z���סC
* �Ѽ�
    | epochs | batch_size | loss | optimizer | threshold |
    |:-:|:-:|:-:|:-:|:-:|
    | 25 | 32 | "binary_crossentropy" | "adam" | 0.5 |
* ���絲�G (Validation on $20\%$ of Training Data)
    | Activation | Validation Loss | Validation F1 Score |
    |:-:|:-:|:-:|
    | Sigmoid | 0.1242 | 0.2906 |
    | Softmax | 0.1145 | 0.0662 |
* �[��M����
    * ���רϥΡusigmoid�v�άO�usoftmax�v�A�uloss�v�������U��
    * ���O�A�usoftmax�v���uf1score�v�o�ܺG�A�]�����צ��h�ӡutag�v���ɭԡA�ҫ��̦h�]�u��q�X�䤤�@�ӡA�Ʀܥi�੼���v���A�̫�|����


#### 3. �иյۤ��R�utags�v���������p(�ƶq)�C
* ���

| Tag | �ƶq | Tag | �ƶq | Tag | �ƶq |
|:-:|:-:|:-:|:-:|:-:|:-:|
| FICTION | 1672 | SPECULATIVE-FICTION | 1448 | NOVEL | 992 |
| SCIENCE-FICTION | 959 | CHILDREN'S-LITERATURE | 777 | FANTASY | 773 |
| MYSTERY | 642 | CRIME-FICTION | 368 | SUSPENSE | 318 |
| YOUNG-ADULT-LITERATURE | 288 | THRILLER | 243 | HISTORICAL-NOVEL | 222 |
| HORROR | 192 | DETECTIVE-FICTION | 178 | ROMANCE-NOVEL | 157 |
| ROMANCE-NOVEL | 137 | ADVENTURE-NOVEL | 109 | NON-FICTION | 102 |
| SPY-FICTION | 75 | ALTERNATE-HISTORY | 72 | COMEDY | 59 |
| AUTOBIOGRAPHY | 51 | BIOGRAPHY | 42 | SHORT-STORY | 41 |
| HISTORY | 40 | COMIC-NOVEL | 37 | SATIRE | 35 |
| MEMOIR | 35 | AUTOBIOGRAPHICAL NOVEL | 31 | WAR-NOVEL | 31 |
| DYSTOPIA | 30 | NOVELLA | 29 | HUMOUR | 18 |
| TECHNO-THRILLER | 18 | HIGH-FANTASY | 15 | APOCALYPTIC-AND-POST-APOCALYPTIC-FICTION | 24 |
| GOTHIC-FICTION | 12 | UTOPIAN-AND-DYSTOPIAN-FICTION | 11 |||
* �[��P�o�{
    * �U���utag�v���ƶq�D�`�������A�q�Q�X�Ө�@�d���ʭӳ���
    * �t�~�A�b�utest�v�����G���A�ƶq�֪��utag�v�X�G���S���Q��X��
    * �����չ�ƶq�֪��utag�v���uup-sampling�v�A���ukaggle public score�v�ϦӤU��


#### 4. �����@�~���ϥΦ�ؤ覡�o��uword embedding�v�H��²��y�z���k�C
* GloVe Embedding�����׵���$50$�������A�]�t�F$40$�U�ӵ��J
* ���V�q���V�m��w�]�t�u����ʬ�v�M�uLinguistic Data Consortium�v���Ѫ��uGigaword�v��Ʈw
* ²��ӻ��A�uGloVe�v���X�F�u�@�{�x�}(�pLSA)�v�M�u�����y�ҵ��f(�pword2vec)�v���u�I�A��X�B�Ρu�����v�M�u�����v���έp�T���ӥͦ����V�q�C�e�̥i�H�ݧ@�ucount-base�v����k�A��̫h�O�uprediction-base�v�������AGloVe�h�O�U���Ҫ��A���իغc��j�j�����V�q�C
* �ܩ󰵪k�A�i�H�յ۱q�uGloVe�v���l����ƨӲz��
    * $J=\sum_{i,j=1}^{|V|} f(\text{c}_{ij})(\text{w}_i\cdot\tilde{\text{w}_j}+b_i+\tilde{b_j}-\log\text{c}_{ij})^2$
    * $\text{w}_i$�M$b_i$�O��e��$t_i$�����V�q�M���m�A$\tilde{\text{w}_j}$�M$\tilde{b_j}$�h�O���ҵ�$t_j$�����U�V�q�M���U���m�A��$c_i$�h�O�q�@�{�x�}���o�쪺�ƭȡA�N���e��$t_i$�M���ҵ�$t_j$�������{�סA���|�H�۰V�m��s
    * $f()$�O�[�v��ơA�j��Y�ӻ֭ȴN�O$1$�A�p�U�ϩҥ�
    ![Minion](http://mmbiz.qpic.cn/mmbiz_png/xWQg0SC4ml0ribk7sR1d8pu3v89Ek1r05makHkbrTAHfibOs46yNUXcfXu7YgYJcujmf1OmGWJWrZH5hhfqGbddw/640?wx_fmt=png&tp=webp&wxfrom=5&wx_lazy=1=200x200)
    * �q�l����Ƥ��A�i�H�o�{���T��Ψ�F������T�A�Y�@�{�x�}��$c_{ij}$�A�P�ɡA�S�M�uword2vec�v�P�˨ϥε��V�q�P���һ��U�V�q�����n�@������
* �V�q�B���m����s��k�N�O���q���ugradient descent�v�A�ñĥΡuadgrad�v�ӸѨM�u���P���ѼơA��s�B���Ī��t�פ��@�w�@�ˡv�����D


#### 5. �դ���ubag of word�v�M�uRNN�v��̦b�����@�~���ĪG���n
* �uTerm Fequency Matrix�v�i�uDNN�v���ҫ�
    | Layer | Parameters |
    |:-:|:-:|
    | Input | `shape = (3000,)` |
    | Dense | `units = 1024` |
    | Dropout | `rate = 0.2` |
    | Activation | `activtion = "relu"` |
    | Dense | `units = 512` |
    | Dropout | `rate = 0.2` |
    | Activation | `activtion = "relu"` |
    | Dense | `units = 256` |
    | Dropout | `rate = 0.2` |
    | Activation | `activtion = "relu"` |
    | Dense | `units = 38`, `activation = "sigmoid"` |
* �uEmbedding�v�f�t�uCNN�v���ҫ� - �ϥΡuFunctional API�v�A�Ҽ{�uBigram�v�B�uTrigram�v�M�u4-gram�v
    | Layer | Parameters | Name | Input |
    |:-:|:-:|:-:|:-:|
    | Input | `shape = (3000,)` | main_input | - |
    | Embedding | `input_dim = 3000`, `output_dim = 50`, `input_length = 50` | emb |main_input |
    | Dropout | `rate = 0.2` | emb_dropout | emb |
    | Conv1D | `units = 128`, `filters = 2`, `activation = "relu"`, `strides = 1` | conv1 | emb_drop |
    | GlobalMaxPooling1D() | - | maxp1 | conv1 |
    | Conv1D | `units = 128`, `filters = 3`, `activation = "relu"`, `strides = 1` | conv2 | emb_drop |
    | GlobalMaxPooling1D() | - | maxp2 | conv2 |
    | Conv1D | `units = 128`, `filters = 4`, `activation = "relu"`, `strides = 1` | conv3 | emb_drop |
    | GlobalMaxPooling1D() | - | maxp3 | conv3 |
    | concatenate | [maxp1, maxp2, maxp3] | merged |  - |
    | Dense | `units = 256` | dense | merged |
    | Dropout | `rate = 0.4` | dropout | dense |
    | Activation | `activtion = "relu"` | activation | dropout |
    | Dense | `units = 38`, `activation = "sigmoid"` | main_output | activation |
* �Ѽ�
    | epochs | batch_size | loss | optimizer | threshold |
    |:-:|:-:|:-:|:-:|:-:|
    | 25 | 32 | "binary_crossentropy" | "adam" | 0.5 |
* ���絲�G (Validation on $20\%$ of Training Data)
    | Model | Validation Loss | Validation F1 Score |
    |:-:|:-:|:-:|
    | RNN-Problem1 | 0.1242 | 0.2906 |
    | DNN | 0.1641 | 0.2588 |
    | CNN | 0.1209 | 0.3079 |
* �[��P�o�{
    * �uTerm Fequency Matrix�v���uDNN�v���ҫ��ܪ����A���ѼƼƶq�ܦh�A�۷�Y�O����A�uValidation�v����{�ϦӤ��p�쥻���uRNN�v�A�]�\�O�]���Ѽƻݭn�A�@�վ�
    * �uCNN�v��������{�̦n�A�@�Τ@�ӡuembedding�v�x�}�A�å浹�T�ءun-gram�v���uCNN�v�A�̫�A�N���G�uconcatenate�v�_�ӡA�i�������P�_�C���L�A�b�ukaggle public score�v����{�o�u�M�uRNN�v�t���h
    

