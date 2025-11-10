# Copyright (2025) Beijing Volcano Engine Technology Ltd.
# SPDX-License-Identifier: MIT

# set(COMPONENT_SRCS
#     VolcRTCDemo.c
#     AudioPipeline.c
#     RtcHttpUtils.c
#     configuration_ap.c
#     network.c
# )
# if (CONFIG_VOLC_RTC_MODE)
#     set(COMPONENT_SRCS ${COMPONENT_SRCS} RtcBotUtils.c)
# endif()
# if (CONFIG_COZE_RTC_MODE)
#     set(COMPONENT_SRCS ${COMPONENT_SRCS} CozeBotUtils.c)
# endif()
# idf_component_register(
#     SRCS ${COMPONENT_SRCS}
#     INCLUDE_DIRS "."
#     REQUIRES esp-sr esp_event esp_netif nvs_flash esp_http_client esp_timer
#              audio_pipeline audio_hal audio_sal audio_stream esp_peripherals
#              audio_board algorithm_stream raw_stream i2s_stream filter_resample
#              fatfs_stream esp_app_format VolcEngineRTCLite
#     EMBED_TXTFILES assets/wifi_configuration_ap.html
# )


set(COMPONENT_SRCS "VolcRTCDemo.c AudioPipeline.c RtcHttpUtils.c configuration_ap.c network.c" )
if (CONFIG_VOLC_RTC_MODE)
    set(COMPONENT_SRCS ${COMPONENT_SRCS} RtcBotUtils.c)
endif()
if (CONFIG_COZE_RTC_MODE)
    set(COMPONENT_SRCS ${COMPONENT_SRCS} CozeBotUtils.c)
endif()
set(COMPONENT_ADD_INCLUDEDIRS .)
set(COMPONENT_EMBED_TXTFILES assets/wifi_configuration_ap.html)

register_component()

# 源文件列表
# set(srcs
#     VolcRTCDemo.c
#     AudioPipeline.c
#     RtcHttpUtils.c
#     configuration_ap.c
#     network.c
# )

# # 按 Kconfig 选项追加源码
# if(CONFIG_VOLC_RTC_MODE)
#     list(APPEND srcs RtcBotUtils.c)
# endif()

# if(CONFIG_COZE_RTC_MODE)
#     list(APPEND srcs CozeBotUtils.c)
# endif()

# # 采用 idf_component_register 新写法，并开启 miniz 以支持压缩
# idf_component_register(
#     SRCS            ${srcs}
#     INCLUDE_DIRS    .
#     EMBED_TXTFILES  assets/wifi_configuration_ap.html
#     REQUIRES
#         esp_wifi
#         esp_netif
#         nvs_flash
#         esp_event
#         esp_http_client
#         driver
#         audio_pipeline
#         audio_stream
#         esp_peripherals
#         # miniz       # 关键：为信令/响应解压提供库，解决 enable_zip 报错
# )

# # 明确开启你代码里的压缩路径（若代码中用该宏控制）
# # target_compile_definitions(${COMPONENT_LIB} PRIVATE LITE_ENABLE_ZIP=1)