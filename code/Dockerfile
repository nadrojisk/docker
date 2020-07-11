FROM codercom/code-server:latest

RUN sudo apt-get update && sudo apt-get -y install python3 python3-pip php wget unzip curl

RUN curl --proto '=https' --tlsv1.2 -sSf https://sh.rustup.rs > tmp
RUN sh tmp -y
