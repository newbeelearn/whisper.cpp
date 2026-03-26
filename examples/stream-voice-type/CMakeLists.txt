if (CMAKE_SYSTEM_NAME MATCHES "Linux")
    set(TARGET whisper-stream-voice-type)
    add_executable(${TARGET} stream-voice-type.cpp)

    include(DefaultTargetOptions)

    target_link_libraries(${TARGET} PRIVATE common common-sdl whisper ${CMAKE_THREAD_LIBS_INIT})

    find_package(X11)
    if (X11_FOUND)
        target_include_directories(${TARGET} PRIVATE ${X11_INCLUDE_DIR})
        target_link_libraries(${TARGET} PRIVATE ${X11_LIBRARIES})
    endif()

    install(TARGETS ${TARGET} RUNTIME)
endif()

if (NOT CMAKE_SYSTEM_NAME MATCHES "Linux")
    add_custom_target(whisper-stream-voice-type
        COMMAND ${CMAKE_COMMAND} -E echo "whisper-stream-voice-type is Linux-only; skipping on ${CMAKE_SYSTEM_NAME}"
        VERBATIM)
endif()
