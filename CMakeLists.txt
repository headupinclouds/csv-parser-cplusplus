# Copyright (c) 2015, Ruslan Baratov
# All rights reserved.

cmake_minimum_required(VERSION 2.8.12)
project(CsvParserCPlusPlus)

option(CSVPARSER_BUILD_EXAMPLES "Build examples" ON)

add_library(
    csv_parser_cplusplus
    include/csv_parser/csv_parser.hpp
    csv_parser.cpp
)

target_include_directories(
    csv_parser_cplusplus
    PUBLIC
    "$<BUILD_INTERFACE:${CMAKE_CURRENT_LIST_DIR}/include>"
    "$<INSTALL_INTERFACE:include>"
)

set(cfg_dest "lib/cmake/CsvParserCPlusPlus")
set(cfg_name CsvParserCPlusPlusTargets)

install(FILES CsvParserCPlusPlusConfig.cmake DESTINATION "${cfg_dest}")
install(TARGETS csv_parser_cplusplus DESTINATION "lib" EXPORT "${cfg_name}")
install(DIRECTORY "include/csv_parser" DESTINATION "include")
install(
    EXPORT "${cfg_name}"
    NAMESPACE CsvParserCPlusPlus::
    DESTINATION "${cfg_dest}"
)

if(CSVPARSER_BUILD_EXAMPLES)
  add_subdirectory(examples)
endif()
