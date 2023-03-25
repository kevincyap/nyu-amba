find_package(Catch2 3 REQUIRED CONFIG)

add_executable(tests)
target_sources(tests PRIVATE ahb/devices/SubDummy/SubDummy.cpp)

nyu_link_sv(tests PRIVATE amba)
nyu_target_verilate(tests
  TOP_MODULES SubDummyWrapper
  ARGS COVERAGE
)

target_link_libraries(tests PRIVATE Catch2::Catch2WithMain)

include(Catch)
catch_discover_tests(tests)

add_subdirectory(ahb)
