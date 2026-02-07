include(FetchContent)

FetchContent_Declare(vault.pthash.essentials
  URL https://github.com/chayden83/jermp.essentials/archive/22c1b51.tar.gz
  URL_MD5 ea55d4d45139cb12e4fc1e95b018b468
  SYSTEM
)

FetchContent_MakeAvailable(vault.pthash.essentials)

vault_add_header_only_library(vault.pthash.bits)

target_sources(vault.pthash.bits PUBLIC FILE_SET HEADERS BASE_DIRS ${PROJECT_SOURCE_DIR}/include FILES
  ${PROJECT_SOURCE_DIR}/include/vault/pthash/bits/darray.hpp
  ${PROJECT_SOURCE_DIR}/include/vault/pthash/bits/cache_line_elias_fano.hpp
  ${PROJECT_SOURCE_DIR}/include/vault/pthash/bits/ranked_sequence.hpp
  ${PROJECT_SOURCE_DIR}/include/vault/pthash/bits/rice_sequence.hpp
  ${PROJECT_SOURCE_DIR}/include/vault/pthash/bits/elias_fano.hpp
  ${PROJECT_SOURCE_DIR}/include/vault/pthash/bits/rank9.hpp
  ${PROJECT_SOURCE_DIR}/include/vault/pthash/bits/bit_vector.hpp
  ${PROJECT_SOURCE_DIR}/include/vault/pthash/bits/util.hpp
  ${PROJECT_SOURCE_DIR}/include/vault/pthash/bits/compact_vector.hpp
  ${PROJECT_SOURCE_DIR}/include/vault/pthash/bits/endpoints_sequence.hpp
  ${PROJECT_SOURCE_DIR}/include/vault/pthash/bits/integer_codes.hpp
  ${PROJECT_SOURCE_DIR}/include/vault/pthash/bits/sdc_sequence.hpp
)
  
target_link_libraries(vault.pthash.bits INTERFACE
  vault::pthash.essentials
)

vault_install_targets(
  TARGETS vault.pthash.bits
)

vault_install_export()
