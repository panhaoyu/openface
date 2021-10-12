FROM bamos/openface
#ADD lfw.tgz /root/openface/data/lfw/aligned
RUN /root/openface/data/download-lfw-subset.sh
RUN mv /root/openface/data/lfw-subset /root/openface/data/lfw
RUN mv /root/openface/data/lfw/raw /root/openface/data/lfw/aligned
ADD lfw-classification.py /root/openface/evaluation/
WORKDIR /root/openface/evaluation
CMD bash
