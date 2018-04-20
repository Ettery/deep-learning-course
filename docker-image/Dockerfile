FROM conda/miniconda3:latest

MAINTAINER Leon van Dyk <leon.vandyk@technovolve.co.za>

RUN pip install --upgrade pip
    
RUN pip install tensorflow pandas matplotlib jupyter

RUN apt-get update && apt-get install -y curl git && \ 
    mkdir ~/downloads && \
    cd ~/downloads && \
    curl -O http://storage.googleapis.com/tensorflow-serving-apt/pool/tensorflow-model-server/t/tensorflow-model-server/tensorflow-model-server_1.5.0_all.deb && \
    dpkg -i tensorflow-model-server_1.5.0_all.deb && \
    apt-get install -f && \
    curl https://pypi.python.org/packages/b5/fc/b703b884743f312603ced4aaddac023e79d38e05b5ece31d1d9aabfdf494/tensorflow_serving_api-1.5.0-py2-none-any.whl > tensorflow_serving_api-1.5.0-py3-none-any.whl && \
    pip install -y tensorflow_serving_api-1.5.0-py3-none-any.whl && \
    cd ~ && \
    rm -r downloads && \
    mkdir -p ~/source/dlwct && \
    cd ~/source/dlwct && \
    git clone https://github.com/dlwct/practicals.git

EXPOSE 8888

WORKDIR ~/source
CMD ["jupyter", "notebook", "--ip=0.0.0.0", "--no-browser", "--allow-root", "--NotebookApp.token="]