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
