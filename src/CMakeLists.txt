set(HEADER_LIST
  "${CMAKE_SOURCE_DIR}/include/aditum/AditumGraph.hpp"
  "${CMAKE_SOURCE_DIR}/include/aditum/FunctionTraits.hpp"
  "${CMAKE_SOURCE_DIR}/include/aditum/RandomRRSetGenerator.hpp"
  "${CMAKE_SOURCE_DIR}/include/aditum/AditumAlgo.hpp"
  "${CMAKE_SOURCE_DIR}/include/aditum/Distribution.hpp"
  "${CMAKE_SOURCE_DIR}/include/aditum/Utility.hpp"
  "${CMAKE_SOURCE_DIR}/include/aditum/io/CapitalScoreFileReader.hpp"
  "${CMAKE_SOURCE_DIR}/include/aditum/io/FileReader.hpp"
  )

# Make an automatic library - will be static or dynamic based on user setting
add_library(aditum ${HEADER_LIST}
  "./AditumGraph.cpp"
  "./CapitalScoreFileReader.cpp"
  "./Utility.cpp"
  "./Distribution.cpp")



target_include_directories(aditum
    PUBLIC
       "${CMAKE_SOURCE_DIR}/include")

target_link_libraries(aditum
  PUBLIC
  networkit
  absl::flat_hash_set
  absl::flat_hash_map
  sfmt)

target_compile_features(aditum PRIVATE cxx_std_17)
