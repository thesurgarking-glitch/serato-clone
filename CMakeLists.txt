cmake_minimum_required(VERSION 3.15)
project(SeratoCloneSampler VERSION 1.0)

# Use C++17
set(CMAKE_CXX_STANDARD 17)
set(CMAKE_CXX_STANDARD_REQUIRED ON)

# Disable formats we don't want to build
set(JUCE_ENABLE_VST2 OFF CACHE BOOL "Disable VST2")
set(JUCE_ENABLE_AU OFF CACHE BOOL "Disable AU")

# Add JUCE subdirectory (assumes JUCE submodule is in serato-clone/JUCE)
add_subdirectory(JUCE)

# Plugin source files
set(SOURCE_FILES
    Source/PluginProcessor.cpp
    Source/PluginProcessor.h
    Source/PluginEditor.cpp
    Source/PluginEditor.h
)

# Define the plugin target
juce_add_plugin(SeratoCloneSampler
    COMPANY_NAME "YourCompany"
    PLUGIN_MANUFACTURER_CODE "SCSP"
    PLUGIN_CODE "SCSP"
    FORMATS VST3 CLAP            # Only VST3 and CLAP
    IS_SYNTH FALSE
    NEEDS_MIDI_INPUT TRUE
    NEEDS_MIDI_OUTPUT FALSE
    COPY_PLUGIN_AFTER_BUILD TRUE
    SOURCES ${SOURCE_FILES}
)

# Link JUCE modules
target_link_libraries(SeratoCloneSampler PRIVATE
    juce::juce_audio_utils
    juce::juce_dsp
)
