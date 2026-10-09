# 과제 스케줄러 — 배포 파일

과제 진척 대시보드·간트 일정 관리 웹 서버(Windows x64, .NET 포함)의 **배포 파일만** 두는 곳입니다.
설치된 서버가 이 레포의 [Releases](../../releases/latest) 에서 새 버전을 확인해 스스로 업데이트합니다. 소스 코드는 여기에 없습니다.

## 처음 설치

1. [Releases](../../releases/latest) 에서 `GanttScheduler-win-x64.zip` 을 받아 서버의 폴더(예: `D:\GanttScheduler`)에 풉니다.
2. `appsettings.Production.json` 에 SQL Server 연결 문자열을 넣습니다. DB 는 미리 만들어 둡니다(테이블은 프로그램이 만듭니다).
3. `install-service.cmd` 를 실행합니다(권한 확인 창에서 "예"). Windows 서비스로 등록되고 바로 시작됩니다.
   - 기본 포트는 80 입니다. 바꾸려면 `install-service.cmd --port 8080`.
4. 브라우저에서 `http://<서버 이름>/` 으로 접속합니다. 처음 이름을 등록한 사람이 관리자가 됩니다.

제거는 `uninstall-service.cmd` (폴더와 데이터는 그대로 둡니다).

## 업데이트

설치한 뒤에는 따로 할 일이 없습니다.

- 서버가 6시간마다 이곳의 최신 릴리스를 확인해 받아 두고, 아무도 쓰지 않는 시간에 스스로 바꿉니다.
- 바로 바꾸려면 관리 > 업데이트 화면에서 "지금 확인" → "지금 적용".
- 서버가 인터넷에 나갈 수 없으면, 릴리스의 zip 을 받아 그 화면에 올리면 됩니다.

각 릴리스의 파일:

| 파일 | 용도 |
|---|---|
| `GanttScheduler-win-x64.zip` | 프로그램 (설치·업데이트 공용) |
| `GanttScheduler-win-x64.zip.sha256` | zip 의 SHA-256 |
| `GanttScheduler.json` | 서버가 새 버전인지 판단하는 정보 (버전, 해시, 크기, 변경 내용) |
