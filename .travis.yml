FROM gcc:latest

RUN apt-get update -y && \
    apt-get install -y libssl-dev

WORKDIR /app

COPY main.cpp .

COPY header_files /app/header_files

RUN g++ -std=c++17 main.cpp -o fileserver -lssl -lcrypto
