cmake_minimum_required(VERSION 3.0)

project(benchmark VERSION 1.0.0 LANGUAGES CXX C)

#### ultimate Libraries ####
add_subdirectory(${CMAKE_CURRENT_SOURCE_DIR}/../../../../SDK_dev/lib build/ultimateMRZ/SDK_dev)

include_directories(
	${CMAKE_CURRENT_SOURCE_DIR}/../../../../SDK_dev/lib/include
)

set(benchmark_SOURCES 
	main.cxx
)

###### The executable ######
add_executable(benchmark ${benchmark_SOURCES})

###### 3rd parties libs ######
target_link_libraries(benchmark ${LIB_LINK_SCOPE} ultimate_mrz-sdk)
add_dependencies(benchmark ultimate_mrz-sdk)

###### Install Libs ######
install(TARGETS benchmark DESTINATION bin)
