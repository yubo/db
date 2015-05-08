add_definitions(-D__DBINTERFACE_PRIVATE -I../include)

add_executable(dbtest dbtest.c ../clib/strerror.c)

target_link_libraries(dbtest db)

enable_testing()
add_test(dbtest ./run.test)

add_subdirectory(hash.tests)
