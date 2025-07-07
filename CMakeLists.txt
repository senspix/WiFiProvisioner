# WiFiProvisioner Component CMakeLists.txt

# Collect all source files
file(GLOB WIFI_PROV_SRCS "src/*.cpp" "*.cpp")

# If sources are in root directory, adjust pattern
if(NOT WIFI_PROV_SRCS)
    file(GLOB WIFI_PROV_SRCS "*.cpp")
endif()

# Register the component
idf_component_register(
    SRCS ${WIFI_PROV_SRCS}
    INCLUDE_DIRS "src" "."
    REQUIRES arduino-esp32 bblanchon__arduinojson esp_wifi esp_netif nvs_flash
)

# Disable format warnings for this component
target_compile_options(${COMPONENT_LIB} PRIVATE -Wno-format)

project(WiFiProvisioner)