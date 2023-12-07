

템플릿 엔진
  Laravel - blade, Spring - JSP, node - EJS와 같은 각 언어의 프레임워크별 템플릿 엔진이라는 것을 쓰게 되는데, 이것은 주로 데이터바인딩, 조건부 렌더링, 반복문등을 사용하여 웹페이지개발을 보다 더 쉽게 구축할 수 있도록 한다. 

laravel프레임 워크의 동작 원리 
  1. Blade: 사용자에게 보여지는 뷰를 담당. HTML과 PHP를 혼합하여 사용, 데이터 동적 삽입, 조건부 렌더링, 반복문등을 사용.
  2. 웹요청을 처리하는 라우트를 정의. 각 라우트는 특정 url패턴에 대응하여, 해당 요청이 들어오면, 지정된 컨트롤러의 메소드를 호출.
  3. Controller: 웹요청을 처리하는 로직을 구현. 주로 데이터베이스에서 데이터를 조회하거나, 데이터를 처리하고, 결과를 뷰에 전달하는 등의 작업을 수행한다.

blade에서의 데이터 삽입법 
  데이터를 넣을떄는 {{ 값 }}, @if, @else, @foreach와 같은 방식으로 작성한다.


Laravel프레임워크 동작원리를 이해하기위한 간단한 흐름 작성
 예제(1) get 요청을 통한 name 값 전달
Greeting url을 통한 
1. 먼저 web.php파일에서 라우트를 정의한다.   <!-- resources/views/greeting.blade.php -->
    <?php
    Route::get('/greeting', 'GreetingController@showGreeting');
    ?>

2. GreetingContoller생성후, showGreeting메소드 정의 및, greeting 뷰를 반환 뷰에 name 데이터를 전달 
    // app/Http/Controllers/GreetingController.php 의 설정 
    <?php
    namespace App\Http\Controllers;
    use Illuminate\Http\Request;
    class GreetingController extends Controller
    {
        public function showGreeting()
        {
        return view('greeting', ['name' => 'James']);
        }
    }
    ?>

3. 마지막으로, greeting.blade.php 뷰를 생성. 이 뷰에서는 blade문법을 사용하여 name 데이터를 출력.

    <html>
     <body>
      <h1>Hello, {{ $name }}</h1>
     </body>
    </html>

예제(2) post 요청을 통한 사용자로부터 입력을 받아 데이터베이스에 저장하고, 그 저장된 값을 가공하여 출력하는 기능을 구현하는 연습.

1.사용자로부터 이름을 입력받는 form  작성 파일 경로 ->  - `resources/views/greeting.blade.php`
    <html>
        <body>
            <form method="POST" action="/greeting">
                @csrf
                <label for="name">Name:</label>
                <input type="text" id="name" name="name">
                <input type="submit" value="Submit">
            </form>
        </body>
    </html>

2. web.php파일에서 라우트를 정의. GET /greeting 요청은 form을 보여주고 POST /greeting 요청은 form 데이터를 처리한다.

    <?php
    Route::get('greeting', 'GreetingController@showForm');
    Route::post('greeting', 'GreetingController@storeAndShowGreeting');
    ?>

3.GreetingController의 class를 수정하여 form을 보여주는 메소드와 form 데이터를 처리하는 메소드를 정의힌다. 
    class GreetingController extends Controller
    {
        public function showForm(){
            return view('greeting')
        }
        public function storeAndShow()
    {
        $request->session()->put('name', $request->name);
        $name = $request->session()->get('name');
        return view('greeting', ['name' => $name]);
    }
    }

## 📂 프로젝트 구조
사내 포털 프로젝트의 주요 디렉토리와 파일들은 다음과 같다:
- `/app`: 애플리케이션의 주요 로직이 위치하는 디렉토리. 컨트롤러, 미들웨어, 모델등 핵심 로직이 포함되어 있음.
- `/config`:애플리케이션의 동작 방식을 결정하기 위한(전역변수등) 위한 설정 파일들.
- `/patch`:버젼별로 sql 관리를 하기위한 디렉토리 
- `/public`:웹 서버의 공개 디렉토리, 웹에서 직접 접근 가능한 이미지, CSS, JavaScript파일 등이 위치.
- `/resources`: 뷰 템플릿, 로컬화 파일 등 사용자UI관련 요소들이 저장되어 있음.
- `/routes`: web.php 라우트 정의가 위치해있음. 사용자의 요청을 알맞은 로직으로 연결하는 역할.
- `/shells`:쉘 스크립트가 저장되는 곳. 서버 관리나 배치 작업등을 위한 스크립트가 위치. 
- `/storage`: 사내포털에서 생성된 파일들이 저장 되는 곳(엑셀 템플렛등)을 하기 위한  세션, 캐시, 로그 등의 데이터 저장용. 
- `/composer-installer.php`:PHP의 종속성 도구 관리를 위한 Composer 설치하는 스크립트.
- `/composer.json`:프로젝트의 PHP 종속성을 정의하는 파일. 필요한 패키지와 그 버젼을 명시하기 위한 JSON파일
- `/.env`: 데이터베이스 연결정보와 같은 환경변수 등을 설정하기 위해 사용.  

## 📂 プロジェクト構造
AIS社内ポータルプロジェクトの主要なディレクトリとファイルは次の通りです。

- `/app`: アプリケーションの主要なロジックが配置されているディレクトリ。コントローラー、ミドルウェア、モデル等主要なロジックが含まれています。
- `/config`:全般的なアプリケーションの動作方式を操作するための(グローバル変数等等等)ファイル。
- `/patch`:　バージョンごとにSQLを管理するためのディレクトリ。
- `/public`:WEBサーバーの公開ディレクトリ、WEBから直接アクセス可能な画像、CSS、Javascriptファイル等が配置されています。
- `/resources`:VIEWテンプレート、ローカライズファイルなど、ユーザーUI関連要素が保存されています。
- `/shells`:シェルスクリプトが保存されている場所。サーバー管理やバッチ処理等のスクリプトが配置されています。
- `/storage`:社内ポータルで生成されたファイルが保存されている場所(Excelテンプレートなど)。セッション、キャッシュ、ログ等のデータ保存用。
- `/composer-installer.php`:PHPの依存関係ツール管理のためのComposerをインストールするスクリプト。
- `/composer.json`:プロジェクトのPHP依存関係を定義するファイル。必要なパッケージとそのバージョンを指定するためのJSONファイル。
- `/.env`:データベースアクセス情報等の環境変数を設定するためのファイル。
AIS-INFO 社内 PORTAL システム
AIS-INFO社内PORTALシステムは、社内の情報共有とコミュニケーションを円滑に行うためのシステムです。

📂 プロジェクト構造
以下は、このプロジェクトの主要なディレクトリとファイルの概要です：