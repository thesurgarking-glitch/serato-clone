cmake_minimum_required(VERSION 3.15)
project(SeratoCloneSampler VERSION 1.0)

set(CMAKE_CXX_STANDARD 17)
set(CMAKE_CXX_STANDARD_REQUIRED ON)

add_subdirectory(JUCE)

set(SOURCE_FILES
    Source/PluginProcessor.cpp
    Source/PluginProcessor.h
    Source/PluginEditor.cpp
    Source/PluginEditor.h
)

juce_add_plugin(SeratoCloneSampler
    COMPANY_NAME "YourCompany"
    PLUGIN_MANUFACTURER_CODE "SCSP"
    PLUGIN_CODE "SCSP"
    FORMATS VST3 CLAP
    SOURCES ${SOURCE_FILES}
)

target_link_libraries(SeratoCloneSampler PRIVATE juce::juce_audio_utils juce::juce_dsp)
