FROM mcr.microsoft.com/devcontainers/python:1-3.8-bookworm

# prepare environment  
RUN \
    apt update && \
    apt-get install -y pipx wget  python3-setuptools libatlas-base-dev gcc git make build-essential libsuitesparse-dev lp-solve

# clone 
RUN \ 
    git clone https://github.com/GeomScale/dingo  && \
    cd dingo  && \
    git submodule update --init

# boost
RUN \
    cd dingo  && \
    wget -O boost_1_76_0.tar.bz2 https://boostorg.jfrog.io/artifactory/main/release/1.76.0/source/boost_1_76_0.tar.bz2  && \
    tar xjf boost_1_76_0.tar.bz2  && \
    rm boost_1_76_0.tar.bz2

# install dependencies
RUN \ 
    cd dingo  && \
    curl -sSL https://install.python-poetry.org | python3 - --version 1.3.2 && \
    export PATH="$HOME/.local/bin:$PATH"  && \
    poetry config virtualenvs.create false && \
    poetry install  && \
    pip3 install numpy scipy

# tests
# poetry run python3 tests/fba.py
# poetry run python3 tests/full_dimensional.py
# poetry run python3 tests/max_ball.py
# poetry run python3 tests/scaling.py
# poetry run python3 tests/sampling.py
# poetry run python3 tests/sampling_no_multiphase.py