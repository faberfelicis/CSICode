# Récupérer tous les fichiers sources
file(GLOB_RECURSE SOURCES 
    "*.cpp"
    "*.cxx"
    "*.c"
)

# Récupérer tous les headers
file(GLOB_RECURSE HEADERS 
    "*.hpp"
    "*.h"
)

# Ajouter les sources au projet
target_sources(${PROJECT_NAME} 
    PRIVATE 
        ${SOURCES}
        ${HEADERS}
)

# Ajouter le dossier src aux include directories
target_include_directories(${PROJECT_NAME}
    PRIVATE
        ${CMAKE_CURRENT_SOURCE_DIR}
)