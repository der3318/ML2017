## �����ǲߧ@�~�� ���i
| �Ǹ� | �t�� | �m�W |
|:-:|:-:|:-:|
| B03902015 | ��u�T | ²޳�w |
#### 1. �Ф�����L�unormalize(rating)�v���t�O�C�û����p��unormalize�v�C
* �ҫ����[�c
    | Layer | Parameters | Name | Input |
    |:-:|:-:|:-:|:-:|
    | Input | `shape=(1,)` | userId | - |
    | Input | `shape=(1,)` | movieId | - |
    | Embedding | `input_dim=6041`, `output_dim=8`, `input_length=1` | uEmb | userId |
    | Flatten | - | uVec | uEmb |
    | Embedding | `input_dim=3953`, `output_dim=8`, `input_length=1` | mEmb | movieId |
    | Flatten | - | mVec | mEmb |
    | Embedding | `input_dim=6041`, `output_dim=1`, `input_length=1` | uEmb2 | userId |
    | Flatten | - | uBias | uEmb2 |
    | Embedding | `input_dim=3953`, `output_dim=8`, `input_length=1` | mEmb2 | movieId |
    | Flatten | - | mBias | mEmb2 |
    | dot | `[uVec, mVec]`, `axes=-1` | umDot | - |
    | add | `[umDot, uBias, mBias]` | output | - |
* �uNormalize�v���覡 - ��urate�v���H$5$(�̤j��)
* ����Ѽ�
    * Batch Size = $128$
    * Epochs = $20$
    * Validation Split = $10\%$
* ���絲�G
    | ���L���W�� | �V�m�L�{ | �̧CMSE |
    |:-:|:-:|:-:|
    | �L | ![Imgur](http://i.imgur.com/iEtGCxF.png) | 0.7564 |
    | �� | ![Imgur](http://i.imgur.com/fIYWCV4.png) | 0.7737 |
* �[��M���
    * �������W�ƪ��ҫ��A���צb�uTrain�v�ΡuValidation�v�l�����U���o�ܧ֡A���b�|�ӡuepochs�v�ɡuValidation�v�N����
    * �S�����W�ƪ��ҫ��A���M�U���o���C�A���ϦӦ�����n�����G
    * ��Ӽҫ����ѼơB�[�c�ۦP�A�u�t�b�uLoss�v���p��A�i�Ӽv�T�uGradient�v���j�p�A���G�o�ۮt�Ƥj


#### 2. ������P���ulatent dimension�v�����G�C
* �ҫ��[�c�P�W�@�D
* ����Ѽ�
    * Batch Size = $128$
    * Epochs = $12$
    * Validation Split = $10\%$
* ���絲�G
![Imgur](http://i.imgur.com/gXH0lla.png =500x400)
* �[��M���
    * �uLatent Dimension�v�O$8$��$16$���ɭԵ��G���n
    * ���פӧC���ܡA�l�����e�����C�F���׶W�L$16$�A�h�ܮe���uoverfit�v�A�i��ݭn�f�t�uearly-stopping�v�Ρuregularization�v�Ӻ��@�uValidation�v�M�uTest�v����{


#### 3. ������L�ubias�v�����G�C
* �ҫ��[�c�P�Ĥ@�D
* ����Ѽ�
    * Batch Size = $128$
    * Epochs = $20$
    * Validation Split = $10\%$
* ���絲�G
    | ���L���m | �V�m�L�{ | �̧CMSE |
    |:-:|:-:|:-:|
    | �� | ![Imgur](http://i.imgur.com/iEtGCxF.png) | 0.7564 |
    | �L | ![Imgur](http://i.imgur.com/IbKGPvQ.png) | 0.7589 |
* �[��M���
    * �����m���ҫ��ѼƵy�L�h�F�@�ǡA�uTrain�v���l�����o����C
    * �b�uValidation�v�W����{�A��̬ۮt���j�A�uMSE�v���୰��$0.75$���k


#### 4. �иյۥΡuDNN�v�ӸѨM�o�Ӱ��D�A�åB�����갵����k(��k����)�C�ä���uMF�v�M�uNN�v�����G�A�Q�׵��G���t���C
* �ҫ��[�c
    | Layer | Parameters | Name | Input |
    |:-:|:-:|:-:|:-:|
    | Input | `shape=(1,)` | userId | - |
    | Input | `shape=(1,)` | movieId | - |
    | Embedding | `input_dim=6041`, `output_dim=8`, `input_length=1` | uEmb | userId |
    | Flatten | - | uVec | uEmb |
    | Embedding | `input_dim=3953`, `output_dim=8`, `input_length=1` | mEmb | movieId |
    | Flatten | - | mVec | mEmb |
    | concatenate | `[uVec, mVec]` | concat | - |
    | Dense | `units=1` | output | concat |
* ����Ѽ�
    * Batch Size = $128$
    * Epochs = $20$
    * Validation Split = $10\%$
* ���絲�G
    | �[�c | �V�m�L�{ | �̧CMSE |
    |:-:|:-:|:-:|
    | FM | ![Imgur](http://i.imgur.com/iEtGCxF.png) | 0.7564 |
    | DNN | ![Imgur](http://i.imgur.com/DH3Hr5W.png) | 0.8233 |
* �[��M���
    * �P�˪��Ѽƶq�A�uDNN�v����uunderfit�v�A���צb�uTrain�v�άO�uValidation�v�A�uMSE�v���W�L$0.8$
    * �q���絲�G�A�i�H�o���A��_�uconcat�v�A�udot�v�������uconsine-similarity�v���N�q�A���H�N��ϥΪ̩M�q�v���ۮe��


#### 5. �иյ۱N�umovie�v���uembedding�v�Ρutsne�v������A�N�umovie category�v��@�ulabel�v�ӧ@��
* �ڿ�F�T�Ӥ���S�O�����O�G�uThriller�v�B�uChrilden's�v�M�uDocumentary�v
* �@�ϵ��G
![Imgur](http://i.imgur.com/AOBFPpn.png =650x500)
* �[��M���
    * �uDocumentary�v�S�O�����A�ڷQ�����ӬO�̯S�O���@���q�v�A�uEmbedding�v�۵M�S�O��X
    * �uThriller�v�X�G��B���������A�i��O�]���A���׬ƻ�˪��q�v�A�h�ֳ�����[�J�@�Ǯ��ơB�~�H�������A�u�O�{�ת��t�O�A�ҥH�S���ܩ��㪺�Q�Ϥ��X��
    * �uChrildren's�v�h���b�����W���������C�]���ൣ�q�v�������i���ٯ�A�Ӥ��A�ҥH��_�uDocumentary�v�A������������S���򶰤�


#### 6. �յۨϥΰ��F�urating�v�H�~���ufeature�v, �û����A���@�k�M���G�A���G�n�a���|�v�T�����C
* �B�~�ϥΪ��ufeature�v�G�~�֡B�ʧO�B¾�~�B�q�v�~���B�q�v����
* ����@�k
    * �M�uMF�v�ۦP�A�]���uUser/Movie Embedding�v�M�uUser/Movie Bias�v
    * ���u¾�~�v�M�u�q�v�����v�A�]�U�ۦ��@�ӡuEmbedding�v(¾�~�ϥΡuEmbedding Layer�v�A�ӹq�v�����ϥΡuDense�v)
    * �C����Ʋ{�b����$4$�ӡuEmbedding�v�A����ӧ@���n�A�@�i�o��$C^4_2=6$�Ӥ��n���G
    * ��$6$�Ӥ��n���G�A�H�Ρu�~�֡v�B�u�ʧO($0$/$1$)�v�M�u�q�v�~���v�A�uconcat�v���@��$9$�����V�q
    * �L�@�h�uDense Layer�v�A����@�ӹ�ơA�[�W�uUser/Movie�v���uBias�v�A�N�O�̫�w��������
* ���絲�G
    * �uValidation MSE�v�̧C�i��$0.74$���k�A�۸����l���uMF�v�A�i�B�F�@��

