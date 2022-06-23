cmake_minimum_required(VERSION 3.16)
project(FFQueue)

if(NOT CMAKE_BUILD_TYPE)
    set(CMAKE_BUILD_TYPE Release)
endif()


# 使用多处理器编译
if(WIN32)
	if(MSVC)
		set(CMAKE_C_FLAGS "${CMAKE_C_FLAGS}  /MP")
		set(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS}  /MP")
		set(VS_STARTUP_PROJECT ${PROJECT_NAME})
	endif(MSVC)
endif(WIN32)

set(source_files 
	${CMAKE_CURRENT_SOURCE_DIR}/src/FFQAbout.cpp 
	${CMAKE_CURRENT_SOURCE_DIR}/src/FFQApp.cpp 
	${CMAKE_CURRENT_SOURCE_DIR}/src/FFQBatchMake.cpp 
	${CMAKE_CURRENT_SOURCE_DIR}/src/FFQBitRatePanel.cpp 
	${CMAKE_CURRENT_SOURCE_DIR}/src/FFQConfigEdit.cpp 
	${CMAKE_CURRENT_SOURCE_DIR}/src/FFQFilterEdit.cpp 
	${CMAKE_CURRENT_SOURCE_DIR}/src/FFQJobEditAdv.cpp 
	${CMAKE_CURRENT_SOURCE_DIR}/src/FFQJobEditAdvCuts.cpp 
	${CMAKE_CURRENT_SOURCE_DIR}/src/FFQJobEditAdvPopup.cpp 
	${CMAKE_CURRENT_SOURCE_DIR}/src/FFQLangEdit.cpp 
	${CMAKE_CURRENT_SOURCE_DIR}/src/FFQMain.cpp 
	${CMAKE_CURRENT_SOURCE_DIR}/src/FFQPresetEdit.cpp 
	${CMAKE_CURRENT_SOURCE_DIR}/src/FFQPresetMgr.cpp 
	${CMAKE_CURRENT_SOURCE_DIR}/src/FFQPresetPanel.cpp 
	${CMAKE_CURRENT_SOURCE_DIR}/src/FFQShowText.cpp 
	${CMAKE_CURRENT_SOURCE_DIR}/src/FFQTimeEdit.cpp 
	${CMAKE_CURRENT_SOURCE_DIR}/src/bin_res.cpp 
	${CMAKE_CURRENT_SOURCE_DIR}/src/filter/AudioDelay.cpp 
	${CMAKE_CURRENT_SOURCE_DIR}/src/filter/AudioTempo.cpp 
	${CMAKE_CURRENT_SOURCE_DIR}/src/filter/BoxBlur.cpp 
	${CMAKE_CURRENT_SOURCE_DIR}/src/filter/ChannelMap.cpp 
	${CMAKE_CURRENT_SOURCE_DIR}/src/filter/ColorBalance.cpp 
	${CMAKE_CURRENT_SOURCE_DIR}/src/filter/ColorMatrix.cpp 
	${CMAKE_CURRENT_SOURCE_DIR}/src/filter/ColorOverlay.cpp 
	${CMAKE_CURRENT_SOURCE_DIR}/src/filter/Crop.cpp 
	${CMAKE_CURRENT_SOURCE_DIR}/src/filter/Curves.cpp 
	${CMAKE_CURRENT_SOURCE_DIR}/src/filter/Custom.cpp 
	${CMAKE_CURRENT_SOURCE_DIR}/src/filter/Decimate.cpp 
	${CMAKE_CURRENT_SOURCE_DIR}/src/filter/Deflicker.cpp 
	${CMAKE_CURRENT_SOURCE_DIR}/src/filter/Deinterlace.cpp 
	${CMAKE_CURRENT_SOURCE_DIR}/src/filter/Dejudder.cpp 
	${CMAKE_CURRENT_SOURCE_DIR}/src/filter/Delogo.cpp 
	${CMAKE_CURRENT_SOURCE_DIR}/src/filter/Deshake.cpp 
	${CMAKE_CURRENT_SOURCE_DIR}/src/filter/DynAudNorm.cpp 
	${CMAKE_CURRENT_SOURCE_DIR}/src/filter/Echo.cpp 
	${CMAKE_CURRENT_SOURCE_DIR}/src/filter/Elbg.cpp 
	${CMAKE_CURRENT_SOURCE_DIR}/src/filter/Equalizer.cpp 
	${CMAKE_CURRENT_SOURCE_DIR}/src/filter/FilterBasePanel.cpp 
	${CMAKE_CURRENT_SOURCE_DIR}/src/filter/Flanger.cpp 
	${CMAKE_CURRENT_SOURCE_DIR}/src/filter/Flip.cpp 
	${CMAKE_CURRENT_SOURCE_DIR}/src/filter/FrameStep.cpp 
	${CMAKE_CURRENT_SOURCE_DIR}/src/filter/HighLowBandPass.cpp 
	${CMAKE_CURRENT_SOURCE_DIR}/src/filter/Hqdn3d.cpp 
	${CMAKE_CURRENT_SOURCE_DIR}/src/filter/Hue.cpp 
	${CMAKE_CURRENT_SOURCE_DIR}/src/filter/Interlace.cpp 
	${CMAKE_CURRENT_SOURCE_DIR}/src/filter/LensCorrection.cpp 
	${CMAKE_CURRENT_SOURCE_DIR}/src/filter/Negate.cpp 
	${CMAKE_CURRENT_SOURCE_DIR}/src/filter/Noise.cpp 
	${CMAKE_CURRENT_SOURCE_DIR}/src/filter/Pad.cpp 
	${CMAKE_CURRENT_SOURCE_DIR}/src/filter/Perspective.cpp 
	${CMAKE_CURRENT_SOURCE_DIR}/src/filter/Phaser.cpp 
	${CMAKE_CURRENT_SOURCE_DIR}/src/filter/Resample.cpp 
	${CMAKE_CURRENT_SOURCE_DIR}/src/filter/Rotate.cpp 
	${CMAKE_CURRENT_SOURCE_DIR}/src/filter/Scale.cpp 
	${CMAKE_CURRENT_SOURCE_DIR}/src/filter/Transpose.cpp 
	${CMAKE_CURRENT_SOURCE_DIR}/src/filter/Unsharp.cpp 
	${CMAKE_CURRENT_SOURCE_DIR}/src/filter/Vignette.cpp 
	${CMAKE_CURRENT_SOURCE_DIR}/src/filter/VolumeAndTone.cpp 
	${CMAKE_CURRENT_SOURCE_DIR}/src/filter/Watermark.cpp 
	${CMAKE_CURRENT_SOURCE_DIR}/src/resource.res 
	${CMAKE_CURRENT_SOURCE_DIR}/src/tools/FFQConcat.cpp 
	${CMAKE_CURRENT_SOURCE_DIR}/src/tools/FFQThumbMake.cpp 
	${CMAKE_CURRENT_SOURCE_DIR}/src/tools/FFQThumbPanel.cpp 
	${CMAKE_CURRENT_SOURCE_DIR}/src/tools/FFQVidStab.cpp 
	${CMAKE_CURRENT_SOURCE_DIR}/src/tools/FFQVideoToGIF.cpp 
	${CMAKE_CURRENT_SOURCE_DIR}/src/utils/FFQBuildCmd.cpp 
	${CMAKE_CURRENT_SOURCE_DIR}/src/utils/FFQCodecInfo.cpp 
	${CMAKE_CURRENT_SOURCE_DIR}/src/utils/FFQCompress.cpp 
	${CMAKE_CURRENT_SOURCE_DIR}/src/utils/FFQConfig.cpp 
	${CMAKE_CURRENT_SOURCE_DIR}/src/utils/FFQConsole.cpp 
	${CMAKE_CURRENT_SOURCE_DIR}/src/utils/FFQConst.cpp 
	${CMAKE_CURRENT_SOURCE_DIR}/src/utils/FFQFilter.cpp 
	${CMAKE_CURRENT_SOURCE_DIR}/src/utils/FFQHash.cpp 
	${CMAKE_CURRENT_SOURCE_DIR}/src/utils/FFQJob.cpp 
	${CMAKE_CURRENT_SOURCE_DIR}/src/utils/FFQLang.cpp 
	${CMAKE_CURRENT_SOURCE_DIR}/src/utils/FFQMisc.cpp 
	${CMAKE_CURRENT_SOURCE_DIR}/src/utils/FFQNvpList.cpp 
	${CMAKE_CURRENT_SOURCE_DIR}/src/utils/FFQPixFmt.cpp 
	${CMAKE_CURRENT_SOURCE_DIR}/src/utils/FFQPreset.cpp 
	${CMAKE_CURRENT_SOURCE_DIR}/src/utils/FFQProbing.cpp 
	${CMAKE_CURRENT_SOURCE_DIR}/src/utils/FFQProcess.cpp 
	${CMAKE_CURRENT_SOURCE_DIR}/src/utils/FFQQueueItem.cpp 
	${CMAKE_CURRENT_SOURCE_DIR}/src/utils/FFQStaticJob.cpp 
	${CMAKE_CURRENT_SOURCE_DIR}/src/utils/FFQStreamMapping.cpp 
	${CMAKE_CURRENT_SOURCE_DIR}/src/utils/FFQTaskBar.cpp 
	${CMAKE_CURRENT_SOURCE_DIR}/src/utils/FFQThumbs.cpp 
	${CMAKE_CURRENT_SOURCE_DIR}/src/utils/FFQTimeValue.cpp 
	${CMAKE_CURRENT_SOURCE_DIR}/src/utils/FFQToolJobs.cpp 
	)

add_executable(${PROJECT_NAME} WIN32
    ${source_files}
	)
    
#target_compile_definitions(${PROJECT_NAME} 
#	PRIVATE "wxUSE_UNICODE /MP"
#	)

#target_include_directories(${PROJECT_NAME}
#    PRIVATE ${CRYPTO_INCLUDE_DIRS}
#    PRIVATE ${CLIENT_INCLUDE_DIRS}
#	)

	
find_package(wxWidgets REQUIRED adv base core gl stc xml)
include(${wxWidgets_USE_FILE})
target_link_libraries(${PROJECT_NAME} LINK_PRIVATE ${wxWidgets_LIBRARIES})

find_package(ZLIB REQUIRED)
target_link_libraries(${PROJECT_NAME} LINK_PRIVATE ${ZLIB_LIBRARIES})

# cd ./src &&  windres.exe -ID:\ProgramFiles\vcpkg\installed\x64-windows\include  -J rc -O coff -i resource.rc -o resource.res
#cmake.exe '-DCMAKE_TOOLCHAIN_FILE=D:/ProgramFiles/vcpkg/scripts/buildsystems/vcpkg.cmake' '-DVCPKG_TARGET_TRIPLET=x64-windows' ..



