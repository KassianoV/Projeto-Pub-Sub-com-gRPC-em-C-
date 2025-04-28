# Projeto Pub/Sub com gRPC em C++

Este projeto implementa um sistema básico de **Publish/Subscribe** usando **gRPC** e **Protobuf** em **C++**. O sistema permite que clientes se inscrevam em tópicos e recebam mensagens em tempo real publicadas nesses tópicos.

## Descrição do projeto

- **Servidor (`server.cpp`)**: Gerencia as assinaturas de tópicos e distribui mensagens para clientes inscritos.
- **Cliente (`client.cpp`)**: Permite que usuários se inscrevam em tópicos e publiquem mensagens.
- **Definição de protocolo (`pubsub.proto`)**: Define mensagens e serviços para a comunicação gRPC.

## Estrutura de Diretórios

```
pubsub_grpc/
├── CMakeLists.txt
├── pubsub.proto
├── server.cpp
└── client.cpp
```

## Tecnologias Utilizadas

- **C++17**
- **gRPC C++**
- **Protocol Buffers (Protobuf)**
- **CMake**

## Instalação e Compilação

### 1. Pré-requisitos

- CMake (>= 3.14)
- gRPC
- Protobuf
- Compilador C++ moderno

No Ubuntu/Debian:

```bash
sudo apt update
sudo apt install -y build-essential cmake pkg-config \
    libprotobuf-dev protobuf-compiler \
    libgrpc++-dev grpc-proto
```

### 2. Compilando o Projeto

```bash
# Clone o repositório
git clone <link-do-repo>
cd pubsub_grpc

# Crie uma pasta de build
mkdir build
cd build

# Gere os arquivos de construção
cmake ..

# Compile o projeto
make
```

Isso gerará dois executáveis:
- `server`
- `client`

## Executando o Projeto

### 1. Rodar o Servidor

```bash
./server
```

Saída esperada:

```
Servidor rodando em 0.0.0.0:50051
```

### 2. Rodar o Cliente

```bash
./client
```

No cliente, você pode:
- Publicar mensagens para o tópico `tech`.
- Receber mensagens em tempo real.

Para sair, digite:

```
exit
```

## Funcionalidades Implementadas

- Publicação de mensagens em tópicos.
- Inscrição com streaming de mensagens.
- Multithreading para publicação e recepção simultâneas.

## Melhorias Futuras

- Suporte a múltiplos tópicos.
- Histórico de mensagens.
- Sistema de autenticação.
- Interface gráfica para o cliente.

## Autor

Desenvolvido por [Seu Nome Aqui].

## Licença

Este projeto está licenciado sob a Licença MIT.

