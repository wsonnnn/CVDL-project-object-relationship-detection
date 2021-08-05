1.yolo部分：
net.py：分为了网络架构，网络损失函数、dataloader、训练函数四个模块。训练时，通过读取VOCdevkit\\VOC2007\\下的JPEGImahes\\和Annotations\\即可开始训练。通过读取Annotations\\内的xml文件，寻找我们需要的信息，并记录在target.txt中
2.test.py：读取测试集 文件夹JPEGImages\\下的图片可以预测，预测结果位于test\\文件夹中
注：
我们在训练yolo时，共进行了2次训练，其中第一次的训练损失会停留在2-3之间，不在下降，而对应的预测结果中会出现class分类不正确的现象，见pdf文件，所以我们进行了第二次训练，但第二次的训练，运行了26个epoch仍没有得出较好的结果，但是由于在第二次的训练时，生成的.pth文件对第一次的模型文件进行了覆盖，所以我们目前有的模型文件是我们第二次的训练结果，但是效果较差。
3loc_fea.ipynb 将开始处path改为对应数据集位置，之后按顺序运行即可
4vgg_net.ipynb 将开始处path、img_path改为数据集对应位置,model1_path\model2_path改为vgg1.h5 vgg2.h5对应位置即可
5sift_svm.ipynb 需要将开始的path 和imgpath改为对应数据集的地址，然后依次运行即可

6.Gaussion.ipynb 文件中有对于sift+gaussion和hog+gaussion两种模型的代码，
     代码逻辑：首先在UIUC_PhrasalRecognitionDataset/VOC3000/Annotations/3000_下找到我们需要的关系所在的图片名称，然后在UIUC_PhrasalRecognitionDataset/VOC3000/JPEGImages/3000_文件夹下找到我们需要的关系所在的图片，通过xml文件中给出的bounding box将图片中的主语和宾语分别进行提取并存入矩阵，之后进行SITF或者HOG特征的提取，根据主语和宾语之间的关系对提取出来的特征建立高斯混合模型，并划分训练集测试集。
在得到train_s和train_o模块中对应函数get_hog_vec和get_vec分别对应使用hog特征和使用sift特征，从前到后直接运行即可。