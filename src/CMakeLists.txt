set(LIBRARY_OUTPUT_PATH ${PROJECT_BINARY_DIR}/lib)
aux_source_directory(. RIME_LUA_SRC)
add_library(rime-lua ${RIME_LUA_SRC})
target_link_libraries(rime-lua ${Rime_LIBRARIES} ${LUA_LIBRARIES})
set_target_properties(rime-lua PROPERTIES VERSION ${RIME_LUA_VERSION} SOVERSION ${RIME_LUA_SOVERSION})
if(XCODE_VERSION)
  set_target_properties(rime-lua PROPERTIES INSTALL_NAME_DIR "@rpath")
endif(XCODE_VERSION)
install(TARGETS rime-lua DESTINATION ${LIB_INSTALL_DIR})
