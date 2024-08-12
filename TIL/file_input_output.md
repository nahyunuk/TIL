# 파일 입출력
### 안드로이드는 애플리케이션이 데이터를 저장할 수 있는 저장소를 두 가지로 제공하고 있다.
## 내부 저장소
- 실행시킨 app을 통해서만 접근이 가능하다.
- app 자체에만 엑서스할 수 있는 민감한 정보를 저장하기 좋다.
- 파일 입출력 : openFileOutput, openFileInput
```
// MODE_PRIVATE : 덮어 씌우기
// MODE_APPEND : 이어서 쓰기
val fos = openFileOutput("data1.dat", MODE_PRIVATE)
val dos = DataOutputStream(fos)
// int형자료 저장
dos.writeInt(100)
// double형자료 저장
dos.writeDouble(11.11)
// bool형자료 저장
dos.writeBoolean(true)
 // 문자열 저장UTF
dos.writeUTF("문자열1")

// 버퍼의 내용을 강제로 출력 장치에 쓴다
dos.flush() 
// 스트림을 닫고 리소스를 해제한다.
dos.close()
```
## 외부 저장소
- 단말기 내부의 공유 영역으로 모든 app이 접근 가능하다.
- 단말기를 컴퓨터에 연결하면 탐색기를 통해 접근할 수 있는 영역을 의미한다.
- Android/data 폴더에 저장되고, 저장된 파일은 다른 app이 접근할 수 없으며 app을 삭제하면 같이 삭제된다.
## getExternalFilesDir
- 외부 저정소의 경로(emulated/Android/data/패키지명/files)를 가져온다.
- getExternalFilesDir 메서드의 매개변수에는 문자열을 넣어줄 수 있으며 files의 하위 폴더 이름을 넣어서 사용할 수 있다.
- null을 넣으면 files까지의 경로가 된다.
### 쓰기
```
val filePath = getExternalFilesDir(null).toString()

val fos = FileOutputStream("${filePath}/data2.dat")
val dos = DataOutputStream(fos)

dos.writeInt(200)
dos.writeDouble(22.22)
dos.writeBoolean(false)
dos.writeUTF("문자열2")

dos.flush()
dos.close()
fos.close()

textView.text = "외부 저장소 앱 데이터 폴더에 저장"
```
### 읽기
```
val fis = FileInputStream("${filePath}/data2.dat")
val dis = DataInputStream(fis)

val data1 = dis.readInt()
val data2 = dis.readDouble()
val data3 = dis.readBoolean()
val data4 = dis.readUTF()

dis.close()
fis.close()
```
## 주요 사용처
### 1. 애플리케이션 데이터 저장
### 애플리케이션의 설정 값, 사용자 데이터 등을 저장하기 위해 파일 입출력을 사용한다. 예를 들어, 사용자의 로그인 정보, 앱 설정, 즐겨찾기 리스트 등을 로컬 파일에 저장할 수 있다.
## 2. 캐싱
### 인터넷에서 받아온 데이터를 캐싱하여 오프라인 상태에서도 사용할 수 있도록 한다. 예를 들어, 이미지나 JSON 데이터를 캐싱하여 네트워크 요청을 줄이고 앱의 성능을 향상시킬 수 있다
## 3. 사용자 파일 관리
### 사용자가 생성하거나 다운로드한 파일을 관리한다. 예를 들어, 텍스트 파일, 이미지, 비디오 등을 저장하고 읽어올 수 있다.
