include(functions/FetchContent_ExcludeFromAll_backport)
include(FetchContent)

if(NOT TARGET ZLIB::ZLIB)
  find_package(ZLIB REQUIRED)
endif()

if(NOT TARGET BZip2::BZip2)
  find_package(BZip2 REQUIRED)
endif()

FetchContent_Declare_ExcludeFromAll(libmpq
    URL https://github.com/diasurgical/libmpq/archive/6a9fbdc7ed3032ff00eb069590da4629bd95da5f.tar.gz
    URL_HASH MD5=5aa2add93b15c1823c18e95768195876
)
FetchContent_MakeAvailable_ExcludeFromAll(libmpq)

add_library(libmpq STATIC
  ${libmpq_SOURCE_DIR}/libmpq/common.c
  ${libmpq_SOURCE_DIR}/libmpq/explode.c
  ${libmpq_SOURCE_DIR}/libmpq/extract.c
  ${libmpq_SOURCE_DIR}/libmpq/huffman.c
  ${libmpq_SOURCE_DIR}/libmpq/mpq.c
  ${libmpq_SOURCE_DIR}/libmpq/wave.c
)

target_include_directories(libmpq PUBLIC ${libmpq_SOURCE_DIR})
target_include_directories(libmpq PRIVATE ${CMAKE_CURRENT_LIST_DIR})

target_link_libraries(libmpq PRIVATE ZLIB::ZLIB BZip2::BZip2)

if(LIBMPQ_FILE_BUFFER_SIZE)
  target_compile_definitions(libmpq PRIVATE "LIBMPQ_FILE_BUFFER_SIZE=${LIBMPQ_FILE_BUFFER_SIZE}")
endif()
