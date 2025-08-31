cmake_minimum_required(VERSION 3.22)
# Enable CMake support for ASM and C languages
enable_language(C ASM)

set(embeddedRTPS_Src
    src/discovery/TopicData.cpp
    src/discovery/ParticipantProxyData.cpp
    src/discovery/SEDPAgent.cpp
    src/discovery/SPDPAgent.cpp
    src/messages/MessageReceiver.cpp
    src/messages/MessageTypes.cpp
    src/ThreadPool.cpp
    src/communication/UdpDriver.cpp
    src/entities/Participant.cpp
    src/entities/Domain.cpp
    src/entities/StatelessReader.cpp
    src/storages/PBufWrapper.cpp
    src/rtps.cpp
    thirdparty/lwip/default_netif.c
    thirdparty/Micro-CDR/src/c/common.c
    thirdparty/Micro-CDR/src/c/types/basic.c
    thirdparty/Micro-CDR/src/c/types/string.c
    thirdparty/Micro-CDR/src/c/types/sequence.c
    thirdparty/Micro-CDR/src/c/types/array.c
)

set(embeddedRTPS_Include_Dirs
    include
    thirdparty/Micro-CDR/include
)

add_library(embeddedRTPS INTERFACE)
target_include_directories(embeddedRTPS INTERFACE ${embeddedRTPS_Include_Dirs})
target_compile_definitions(embeddedRTPS INTERFACE ${MX_Defines_Syms})

target_sources(${CMAKE_PROJECT_NAME} PRIVATE ${embeddedRTPS_Src})
