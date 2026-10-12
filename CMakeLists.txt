idf_component_register(SRCS "bitmap.c" "capi_video.cpp"
                    INCLUDE_DIRS "include"
                    PRIV_REQUIRES driver esp_driver_dac esp_driver_gpio esp_hw_support)

# 上游视频代码依赖 ESP32 寄存器和旧式 C++ 写法；这些告警不影响其既有时序逻辑。
target_compile_options(${COMPONENT_LIB} PRIVATE
    -Wno-error=missing-field-initializers
    -Wno-error=xor-used-as-pow
    -Wno-error=attributes
    -Wno-error=volatile
    -Wno-error=implicit-fallthrough
)
