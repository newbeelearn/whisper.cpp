if (WHISPER_SDL2)
    set(TARGET whisper-stream-voice-type)
    add_executable(${TARGET} stream-voice-type.cpp)

    include(DefaultTargetOptions)

    target_link_libraries(${TARGET} PRIVATE common common-sdl whisper ${CMAKE_THREAD_LIBS_INIT})

    if (UNIX AND NOT APPLE)
        find_package(X11)
        if (X11_FOUND)
            target_include_directories(${TARGET} PRIVATE ${X11_INCLUDE_DIR})
            target_link_libraries(${TARGET} PRIVATE ${X11_LIBRARIES})
        endif()
    endif()

    install(TARGETS ${TARGET} RUNTIME)
endif ()
