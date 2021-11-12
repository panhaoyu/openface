FROM bamos/openface

#要注意Dockerfile的特性：缓存！一定要学习，有缓存！
#如果前面的发生变化后，要看是否执行了命令！
#事实上RUN脚本都是可以直接在docker里面create terminal然后在里面执行的，看心情
#我写在这里是为了偷懒，这样可以每次不用进去敲代码
#ADD lfw.tgz /root/openface/data/lfw/aligned
ADD data /root/openface/data/lfw/source
#RUN /root/openface/data/download-lfw-subset.sh
#RUN mv /root/openface/data/lfw-subset /root/openface/data/lfw
#RUN mv /root/openface/data/lfw/raw /root/openface/data/lfw/aligned
ADD lfw-classification.py /root/openface/evaluation/
#执行这个脚本，使用绝对路径就好
RUN /root/openface/util/align-dlib.py /root/openface/data/lfw/source/ align outerEyesAndNose /root/openface/data/lfw/aligned --size 96
WORKDIR /root/openface/evaluation
#执行命令然后进入bash，也就是每次启动的时候自动训练，这都是为了偷懒，因为在外面写代码要比切进去写代码舒服得多
#这一步写在了CMD里，这样可以看到输出结果，也就是训练进度
CMD python lfw-classification.py temp; bash