cmake_minimum_required(VERSION 3.14)

project(pubsub_grpc)

set(CMAKE_CXX_STANDARD 17)

# Busca Protobuf e gRPC
find_package(Protobuf REQUIRED)
find_package(gRPC REQUIRED)

# Gera código a partir do .proto
set(PROTO_FILE pubsub.proto)

protobuf_generate_cpp(PROTO_SRCS PROTO_HDRS ${PROTO_FILE})
grpc_generate_cpp(GRPC_SRCS GRPC_HDRS ${PROTO_FILE})

# Adiciona os arquivos gerados
add_library(pubsub_proto
    ${PROTO_SRCS}
    ${PROTO_HDRS}
    ${GRPC_SRCS}
    ${GRPC_HDRS}
)

target_link_libraries(pubsub_proto
    gRPC::grpc++
    protobuf::libprotobuf
)

# Executável do servidor
add_executable(server server.cpp)
target_link_libraries(server pubsub_proto)

# Executável do cliente
add_executable(client client.cpp)
target_link_libraries(client pubsub_proto)