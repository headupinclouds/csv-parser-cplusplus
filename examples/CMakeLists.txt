# Copyright (c) 2015, Ruslan Baratov
# All rights reserved.

add_executable(driver driver.cpp)
target_link_libraries(driver PRIVATE csv_parser_cplusplus)
