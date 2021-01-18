FROM continuumio/miniconda3:latest

RUN apt-get update && \
    apt-get install -y --no-install-recommends build-essential && \
    rm -rf /var/lib/apt/lists/*

RUN conda create -n myenv python=3.5

SHELL ["conda", "run", "-n", "myenv", "/bin/bash", "-c"]

RUN conda install -y pytorch=0.4.1 -c pytorch && \
    conda install -y -c anaconda scikit-learn nose && \
    conda clean -y -a

COPY torchMoji /home/haggingface/torchMoji
RUN cd /home/huggingface/torchMoji && \
    pip install -e . && \
    cd tests && \
    nosetests -v && \
    cd /home/