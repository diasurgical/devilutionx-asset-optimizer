include(functions/FetchContent_ExcludeFromAll_backport)
include(FetchContent)

set(ENABLE_INSTALL OFF)
FetchContent_Declare_ExcludeFromAll(
  dvl_gfx
  URL https://github.com/diasurgical/clx-conversion-tools/archive/refs/tags/1.3.0.tar.gz
  URL_HASH MD5=e129a5581d4879a42b9f808ae35a28b9
)
FetchContent_MakeAvailable_ExcludeFromAll(dvl_gfx)
