add_definitions(-D__DBINTERFACE_PRIVATE -I../../include)

add_executable(driver2 driver2.c)
target_link_libraries(driver2 db)

add_executable(tcreat3 tcreat3.c)
target_link_libraries(tcreat3 db)

add_executable(tdel tdel.c)
target_link_libraries(tdel db)

add_executable(thash4 thash4.c)
target_link_libraries(thash4 db)

add_executable(tread2 tread2.c)
target_link_libraries(tread2 db)

add_executable(tseq tseq.c)
target_link_libraries(tseq db)

add_executable(tverify tverify.c)
target_link_libraries(tverify db)

