cmake_minimum_required(VERSION 3.10)
project(tp0 C)

set(CMAKE_C_STANDARD 11)

# 1) Include path para los headers de commons
include_directories(${CMAKE_SOURCE_DIR}/so-commons-library/src/commons)

# 2) Donde está la libcommons.so compilada
link_directories(${CMAKE_SOURCE_DIR}/so-commons-library/src/build)

include_directories(so-commons-library/src)

# 3) Ejecutable CLIENT
add_executable(client
        client/src/client.c
        client/src/utils.c
)
target_link_libraries(client
        commons       # libcommons.so
        readline      # -lreadline
        pthread       # -lpthread
        m             # -lm
)

# 4) Ejecutable SERVER
add_executable(server
        server/src/server.c
        server/src/utils.c
)
target_link_libraries(server
        commons
        readline
        pthread
        m
)
