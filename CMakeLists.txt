cmake_minimum_required(VERSION 3.5)
project(edlines)

include_directories(${CMAKE_CURRENT_SOURCE_DIR}/edlines)
add_definitions(-std=c++14 -O3)

file(GLOB src 
        "${CMAKE_CURRENT_SOURCE_DIR}/edlines/edlines.cpp"
        "${CMAKE_CURRENT_SOURCE_DIR}/c66/VXLIB_sobel_3x3_i8u_o16s_o16s_cn.c"


)

add_library(edline STATIC ${src}
    "${CMAKE_CURRENT_SOURCE_DIR}/edlines"
    "${CMAKE_CURRENT_SOURCE_DIR}/c66"
)


add_executable(edlines ${CMAKE_CURRENT_SOURCE_DIR}/test.cpp)
target_link_libraries(edlines
    edline
    # below is opencv
    -lopencv_cudabgsegm -lopencv_cudaobjdetect -lopencv_cudastereo -lopencv_stitching -lopencv_cudafeatures2d -lopencv_superres -lopencv_cudacodec -lopencv_videostab -lopencv_cudaoptflow -lopencv_cudalegacy -lopencv_cudawarping -lopencv_aruco -lopencv_bgsegm -lopencv_bioinspired -lopencv_ccalib -lopencv_dnn -lopencv_dpm -lopencv_fuzzy -lopencv_hdf -lopencv_line_descriptor -lopencv_optflow -lopencv_plot -lopencv_reg -lopencv_saliency -lopencv_stereo -lopencv_structured_light -lopencv_rgbd -lopencv_viz -lopencv_surface_matching -lopencv_tracking -lopencv_datasets -lopencv_text -lopencv_face -lopencv_xfeatures2d -lopencv_shape -lopencv_video -lopencv_ximgproc -lopencv_calib3d -lopencv_features2d -lopencv_flann -lopencv_xobjdetect -lopencv_objdetect -lopencv_ml -lopencv_xphoto -lippicv -lopencv_highgui -lopencv_videoio -lopencv_photo -lopencv_imgcodecs -lopencv_cudaimgproc -lopencv_cudafilters -lopencv_imgproc -lopencv_cudaarithm -lopencv_core -lopencv_cudev
)