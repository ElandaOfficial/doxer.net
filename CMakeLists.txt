cmake_minimum_required(VERSION 3.21)

set(PROJECT_INFO_NAME    "doxer.net")
set(PROJECT_INFO_ID      "DoxerNet")
set(PROJECT_INFO_SUMMARY "A Doxygen documentation server that allows sending documentation data over http-requests.")
set(PROJECT_INFO_SITE    "https://github.com/ElandaOfficial/doxer.net")
set(PROJECT_INFO_VERSION "0.1.0")

set(CMAKE_CXX_STANDARD          17)
set(CMAKE_CXX_STANDARD_REQUIRED 17)

project(${PROJECT_INFO_ID}
        VERSION      ${PROJECT_INFO_VERSION}
        DESCRIPTION  "${PROJECT_INFO_SUMMARY}"
        HOMEPAGE_URL "${PROJECT_INFO_SITE}"
        LANGUAGES    C CXX)

add_subdirectory(lib)

juce_add_console_app(${PROJECT_INFO_ID}
        PRODUCT_NAME      "${PROJECT_INFO_NAME}"
        VERSION           ${PROJECT_INFO_VERSION}
        ICON_BIG          ""
        ICON_SMALL        ""
        COMPANY_COPYRIGHT "Elanda 2022"
        COMPANY_NAME      "Elanda"
        COMPANY_WEBSITE   "${PROJECT_INFO_SITE}"
        COMPANY_EMAIL     "elendaofficial@gmail.com"
        NEEDS_CURL        true
        NEEDS_WEB_BROWSER false)

add_subdirectory(src)
add_subdirectory(res)

target_link_libraries(${PROJECT_INFO_ID}
    PRIVATE
        juce::juce_core
        jaut::jaut_core)