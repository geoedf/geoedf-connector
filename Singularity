BootStrap: docker
From: continuumio/miniconda3

%files

    framework/ /tmp
    faoinput/ /tmp
    datetimefilter/ /tmp
    run-workflow-stage.sh /usr/local/bin/

%environment
    export PYTHONPATH=/usr/local/lib/python3.7/dist-packages:$PYTHONPATH
    export PATH=/opt/conda/bin:/opt/conda/envs/faoinput/bin:/opt/conda/envs/datetimefilter/bin:$PATH

%post

    apt-get update && apt-get -y install python3-pip wget curl

    cd /tmp/framework && pip3 install .

    chmod -R go+rX /usr/local/lib/python3.7/dist-packages

    chmod a+x /usr/local/bin/run-workflow-stage.sh

    export PATH=/opt/conda/bin:$PATH
    echo ". /opt/conda/etc/profile.d/conda.sh" >> ~/.bashrc

    conda create --name faoinput

    cd /tmp/faoinput && conda install -n faoinput pip && conda run -n faoinput /opt/conda/envs/faoinput/bin/pip install .

    conda create --name datetimefilter
    
    cd /tmp/datetimefilter && conda install -n datetimefilter pip && conda run -n datetimefilter /opt/conda/envs/datetimefilter/bin/pip install .
