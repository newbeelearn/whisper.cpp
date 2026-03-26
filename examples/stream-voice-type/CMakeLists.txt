if (WHISPER_SDL2)
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
    else()
        message(STATUS "Skipping whisper-stream-voice-type on ${CMAKE_SYSTEM_NAME}: this example currently targets Linux")
    endif()
endif ()
