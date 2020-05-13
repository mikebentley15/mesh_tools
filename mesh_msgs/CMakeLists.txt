cmake_minimum_required(VERSION 3.5)
project(mesh_msgs)

set(CMAKE_CXX_STANDARD 14)

find_package(ament_cmake REQUIRED)
find_package(rosidl_default_generators REQUIRED)
find_package(geometry_msgs REQUIRED)
find_package(sensor_msgs REQUIRED)
find_package(std_msgs REQUIRED)

rosidl_generate_interfaces(${PROJECT_NAME}
    msg/Feature.msg
    msg/MeshFaceCluster.msg
    msg/MeshFaceClusterStamped.msg
    msg/MeshFeatures.msg
    msg/MeshGeometry.msg
    msg/MeshGeometryStamped.msg
    msg/MeshMaterial.msg
    msg/MeshMaterials.msg
    msg/MeshMaterialsStamped.msg
    msg/MeshTexture.msg
    msg/MeshVertexColors.msg
    msg/MeshVertexColorsStamped.msg
    msg/MeshVertexCosts.msg
    msg/MeshVertexCostsStamped.msg
    msg/MeshVertexTexCoords.msg
    msg/TriangleIndices.msg
    msg/TriangleMesh.msg
    msg/TriangleMeshStamped.msg
    msg/VectorField.msg
    msg/VectorFieldStamped.msg
    srv/GetGeometry.srv
    srv/GetLabeledClusters.srv
    srv/GetMaterials.srv
    srv/GetTexture.srv
    srv/GetUUID.srv
    srv/GetVertexColors.srv
    srv/GetVertexCosts.srv
  DEPENDENCIES
    geometry_msgs
    sensor_msgs
    std_msgs
)

ament_package()
