if(BUILD_ASSIMP_SUPPORT)
  set(ESP_BUILD_ASSIMP_SUPPORT ON)
endif()

if(BUILD_PTEX_SUPPORT)
  set(ESP_BUILD_PTEX_SUPPORT ON)
endif()

if(BUILD_WITH_CUDA)
  set(ESP_BUILD_WITH_CUDA ON)
endif()

if(BUILD_WITH_BULLET)
  set(ESP_BUILD_WITH_BULLET ON)
endif()

if(BUILD_WITH_VHACD)
  set(ESP_BUILD_WITH_VHACD ON)
endif()

if(BUILD_WITH_BACKGROUND_RENDERER)
  set(ESP_BUILD_WITH_BACKGROUND_RENDERER ON)
endif()

configure_file(
  ${CMAKE_CURRENT_SOURCE_DIR}/configure.h.cmake ${CMAKE_CURRENT_BINARY_DIR}/configure.h
)

find_package(Corrade REQUIRED Utility)
find_package(MagnumIntegration REQUIRED Eigen)

add_library(
  core STATIC
  Buffer.cpp
  Buffer.h
  Check.cpp
  Check.h
  Configuration.cpp
  Configuration.h
  Esp.cpp
  Esp.h
  Logging.cpp
  Logging.h
  managedContainers/AbstractFileBasedManagedObject.h
  managedContainers/AbstractManagedObject.h
  managedContainers/ManagedContainer.h
  managedContainers/ManagedContainerBase.cpp
  managedContainers/ManagedContainerBase.h
  managedContainers/ManagedFileBasedContainer.h
  Random.h
  Spimpl.h
  Utility.h
)

target_link_libraries(
  core
  PUBLIC Corrade::Utility Magnum::Magnum MagnumIntegration::Eigen
)

target_include_directories(core PUBLIC ${PROJECT_BINARY_DIR})
