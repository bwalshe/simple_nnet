set(CMAKE_RUNTIME_OUTPUT_DIRECTORY ${CMAKE_BINARY_DIR}/bin)
set(CMAKE_ARCHIVE_OUTPUT_DIRECTORY ${CMAKE_BINARY_DIR}/lib)
add_library(basicnnet BasicNeuralNet.cpp IdxLoader.cpp ImageSampler.cpp Layer.cpp)
target_include_directories(basicnnet PUBLIC ../include)
target_link_libraries (basicnnet Eigen3::Eigen  ${ZLIB_LIBRARIES})
target_compile_features(basicnnet PUBLIC cxx_std_11)
set_target_properties(basicnnet PROPERTIES CXX_EXTENSIONS OFF)
add_executable(train main.cpp)
target_link_libraries(train basicnnet)