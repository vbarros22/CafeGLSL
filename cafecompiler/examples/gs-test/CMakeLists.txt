cmake_minimum_required(VERSION 3.13)
project(cafeglsl_gs_test CXX)

# Configure with devkitPro's wrapper and point it at a CafeGLSL install, e.g.:
#   /opt/devkitpro/portlibs/wiiu/bin/powerpc-eabi-cmake -S . -B build \
#       -Dcafeglsl_DIR=<prefix>/lib/cmake/cafeglsl
find_package(cafeglsl REQUIRED)

add_executable(cafeglsl_gs_test main.cpp)
set_target_properties(cafeglsl_gs_test PROPERTIES CXX_STANDARD 17 CXX_STANDARD_REQUIRED ON)
target_link_libraries(cafeglsl_gs_test PRIVATE whb cafeglsl::cafeglsl)

wut_create_rpx(cafeglsl_gs_test)
wut_create_wuhb(cafeglsl_gs_test
   NAME "CafeGLSL GS test"
   SHORTNAME "GS test"
   AUTHOR "CafeGLSL")
