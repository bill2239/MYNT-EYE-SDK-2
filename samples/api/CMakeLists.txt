# Copyright 2018 Slightech Co., Ltd. All rights reserved.
#
# Licensed under the Apache License, Version 2.0 (the "License");
# you may not use this file except in compliance with the License.
# You may obtain a copy of the License at
#
#     http://www.apache.org/licenses/LICENSE-2.0
#
# Unless required by applicable law or agreed to in writing, software
# distributed under the License is distributed on an "AS IS" BASIS,
# WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
# See the License for the specific language governing permissions and
# limitations under the License.

get_filename_component(DIR_NAME ${CMAKE_CURRENT_LIST_DIR} NAME)

set_outdir(
  "${OUT_DIR}/lib/${DIR_NAME}"
  "${OUT_DIR}/lib/${DIR_NAME}"
  "${OUT_DIR}/bin/${DIR_NAME}"
)

## camera_a

make_executable(camera_a
  SRCS camera.cc
  LINK_LIBS mynteye ${OpenCV_LIBS}
  DLL_SEARCH_PATHS ${PRO_DIR}/_install/bin ${OpenCV_LIB_SEARCH_PATH}
)

## get_depth_with_region

if(OpenCV_VERSION VERSION_LESS 4.0)

make_executable(get_depth_with_region
  SRCS get_depth_with_region.cc
  LINK_LIBS mynteye ${OpenCV_LIBS}
  DLL_SEARCH_PATHS ${PRO_DIR}/_install/bin ${OpenCV_LIB_SEARCH_PATH}
)

endif()
