# FBX
autodesk사에서 개발한 3D파일 형식
    
    3D 모델, 애니메이션, 텍스처, 카메라, 조명 등 다양한 3D 데이터를 저장

## 특징

1. 광범위한 호환성: 여러 3D 소프트웨어 (Maya, 3ds Max, Blender, Unity, Unreal Engine 등)에서 FBX 파일을 사용하여 데이터를 교환할 수 있습니다.

2. 다양한 데이터 저장 가능: 3D 모델 외에도 애니메이션, 조명, 카메라, 텍스처 등 복잡한 씬 정보를 한 파일에 저장할 수 있습니다.

3. 텍스처와 애니메이션 지원: FBX는 정적 모델뿐 아니라 캐릭터 애니메이션, 모핑, 스키닝, 카메라 애니메이션 등 다양한 애니메이션 데이터를 지원합니다.

4. 이식성: FBX는 텍스트 기반의 ASCII 형식과 이진(binary) 형식 두 가지 형식으로 저장할 수 있어 파일 크기와 이식성을 조절할 수 있습니다.

# FBX SDK
개발자가 FBX 파일을 작업할 수 있도록 도와주는 소프트웨어 라이브러리

FBX 형식으로 저장된 3D 자산과 애니메이션을 읽고, 쓰고, 수정할 수 있는 도구들을 제공

1. 3D 모델
    - 정점(Vertex), 면(Faces), 법선(Normals), UV 좌표 등 3D 메쉬 데이터를 읽고 쓸 수 있습니다.
    - 복잡한 3D 모델을 프로그램적으로 생성하거나 수정 가능.

2. 애니메이션(Animation)
    - 키프레임 애니메이션: 개체의 위치, 회전, 스케일링 등 트랜스폼 정보를 시간 축에 따라 읽고 쓰기.
    - 골격 애니메이션(Skeletal Animation): 본(bone) 시스템 및 스키닝(skinning) 데이터를 처리할 수 있습니다.
    - 모핑(Morphing) 또는 블렌드 쉐이프(Blend Shape): 표정 변화나 기타 애니메이션 효과를 위한 모핑 데이터를 다룰 수 있습니다.

3. 텍스처(Texture) 및 재질(Material)
    - FBX 파일 내에 저장된 텍스처 맵 (예: 컬러, 반사, 범프, 노멀 맵 등)을 읽고 수정 가능.
    - 재질(Material) 속성(예: 확산 반사, 투명도, 반사율 등)을 조작하여 표면의 시각적 속성을 제어할 수 있습니다.

4. 카메라(Camera)
    - 카메라의 위치, 회전, 시야각(FOV), 클리핑 거리 등의 정보를 읽고 쓸 수 있어, 카메라 애니메이션을 조작하거나 새 카메라를 추가할 수 있습니다.

5. 조명(Lighting)
    - FBX 파일에 포함된 조명 정보 (예: 광원 타입, 강도, 색상, 위치, 방향 등)를 읽고 수정 가능.
    - 점광(Point Light), 직사광(Directional Light), 스포트라이트(Spotlight) 등의 다양한 조명 데이터를 조작할 수 있습니다.

6. 계층 구조(Scene Hierarchy)
    - 3D 씬에서 객체들의 계층적 관계(부모-자식 관계)를 접근할 수 있습니다.
    - 씬의 트리 구조를 탐색하고 각 객체의 트랜스폼 및 관련 데이터를 수정 가능.

7. 변환(Transform) 정보
    - 각 객체의 위치(Position), 회전(Rotation), 스케일(Scale) 정보도 수정하거나 새로운 값을 설정할 수 있습니다.

8. 메타데이터(Metadata)
    - FBX 파일에 포함된 추가적인 메타 정보를 읽고 쓸 수 있습니다. 예를 들어 파일 작성자 정보, 타임스탬프 등.

9. 물리(Physics) 및 기타 속성
    - 물리 속성(질량, 중력 적용 여부 등)이나 충돌 데이터 등도 지원하는 형식에서는 처리할 수 있습니다.