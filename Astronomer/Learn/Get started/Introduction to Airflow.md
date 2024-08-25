# Apache Airflow 소개

[Apache Airflow](https://airflow.apache.org)는 데이터 파이프라인을 프로그래밍으로 작성, 스케줄링, 모니터링하기 위한 오픈소스 툴 입니다. 매달 수백만 명의 신규 및 복귀 사용자가 Airflow를 다운로드하며 대규모의 활발한 오픈 소스 [커뮤니티](https://airflow.apache.org/community)가 있습니다. Airflow의 핵심 원칙은 데이터 파이프라인을 코드로 정의하여 동적이고 확장 가능한 워크플로우를 만드는데 있습니다.

이 가이드는 Apache Airflow와 핵심 개념에 대한 소개를 제공합니다. 다음에 대해 알아보게 됩니다:
- Apache Airflow의 역사
- 왜 Airflow를 사용해야 할까요?
- Airflow의 일반적인 사용 사례
- Airflow를 실행하는 방법
- Airflow의 중요 컨셉
- Airflow에 대해 자세히 알아볼 수 있는 리소스를 찾을 수 있는 곳

# 사전 지식

이 가이드를 최대한 활용하기 위해선 다음 사항을 이해하고 있어야합니다.
-  기본 파이썬. [파이썬 문서](https://docs.python.org/3/tutorial/index.html)를 참조하세요.

# Airflow의 역사
지난 10년 동안 Airflow는 데이터 오케스트레이션을 위한 오픈 소스 표준으로 성장했습니다.

- 2015: Airflow는 Airbnb에서 오픈 소스 프로젝트로 시작되었습니다. 2015년에 Airbnb는 빠르게 성장하고 매일 생성되는 방대한 양의 내부 데이터를 관리하는데 어려움을 겪었습니다. 강력한 스케줄링 도구에 대한 필요성을 충족하기 위해 [Maxime Beauchemin](https://maximebeauchemin.medium.com)은 Airflow를 만들어 Airbnb가 배치 데이터 파이프라인을 빠르게 작성, 반복 및 모니터링할 수 있도록 했습니다.
- 2016년: Airflow가 공식적으로 Apache Foundation Incubator에 가입했습니다.
- 2019년: Airflow가 최상위 Apache 프로젝트로 선정되었습니다.
- 2020년: Airflow 2.0이 출시되어 주요 업그레이드와 강력한 기능이 새로 추가 되었습니다.
- 2020~현재: 커뮤니티가 더욱 강력해짐에 따라 Airflow 채택이 꾸준히 가속화되고 있습니다. 지속적인 릴리즈에는 새로운 기능과 개선사항이 추가됩니다.


# 왜 Airflow를 사용하는가?
[Apache Airflow](https://airflow.apache.org/index.html)는 워크플로우를 프로그래밍 방식으로 작성, 스케줄링 및 모니터링 하기 위한 플랫폼입니다. 특히 복잡한 파이프라인을 만들고 조율하는데 유용합니다.

데이터 오케스트레이션은 모든 최신 데이터 스택의 핵심에 있으며 데이터 파이프라인의 정교한 자동화를 제공합니다. 오케스트레이션을 통해 데이터 파이프라인의 작업이 서로를 인식하게 되고 데이터 팀은 중앙에서 워크플로를 모니터링, 편집 및 문제 해결을 할 수 있습니다.

Airflow는 다음과 같은 많은 이점을 제공합니다:

- 도구 불가지론 : Airflow는 API를 통한 연결을 허용하는 데이터 생태계의 모든 애플리케이션에 연결할 수 있습니다. 사전 구축된 [연산자](https://www.astronomer.io/docs/learn/what-is-an-operator)는 많은 일반적인 데이터 도구에 연결하기 위해 존재합니다.
- 높은 확장성 : Airflow 파이프라인은 Python으로 작성되므로 기존 코드베이스를 기반으로 빌드하고 Airflow의 기능을 확장하여 필요에 맞게 만들 수 있습니다. Python에서 할 수 있는 모든 것은 Airflow에서도 할 수 있습니다.
- 무한한 확장성 : 컴퓨팅 능력이 충분하다면 파이프라인이 아무리 복잡하더라도 필요한 만큼 많은 프로세스를 조정할 수 있습니다.
- 동적 데이터 파이프라인 : Airflow는 런타임에 처리하는 데이터에 따라 워크플로를 조정하는 [동적 작업](https://www.astronomer.io/docs/learn/dynamic-tasks)을 생성하는 기능을 제공합니다.
- 활동적인 OSS 커뮤니티 : 수백만 명의 사용자와 수천 명의 기여자와 함께 Airflow는 지속되고 성장할 것입니다. [Airflow Slack](https://apache-airflow-slack.herokuapp.com/)에 가입하여 커뮤니티의 일원이 되세요.
- 관찰 가능성 : Airflow UI는 모든 데이터 파이프라인에 대한 즉각적인 개요를 제공하고 전체 데이터 생태계의 워크플로에 대한 진실의 원천을 제공할 수 있습니다.


# Airflow 사용 사례
규모와 유형에 관계없이 많은 기업의 데이터 전문가들이 Airflow를 사용하고 있습니다. 데이터 엔지니어, 데이터 사이언티스트, ML 엔지니어, 데이터 분석가 모두 복잡한 종속성 웹에서 데이터에 대한 작업을 수행해야 합니다. Airflow를 사용하면 사용중인 도구와 파이프라인이 얼마나 복잡한지와 상관없이 단일 플랫폼에서 이러한 작업과 종속성을 오케스트레이션할 수 있습니다.

![Airflow use cases](https://www.astronomer.io/docs/assets/images/intro-to-airflow_airflow_in_ecosystem-3abe77d0043faf34f10ab8d510388e54.png)

Airflow의 몇 가지 일반적인 사용 사례는 다음과 같습니다:
- ETL/ELT: [Airflow 사용자의 90%](https://airflow.apache.org/survey/)가 추출-변환-로드(ETL) 및 추출-로드-전송(ELT)패턴에 Airflow를 사용합니다. 이러한 파이프라인은 종종 중요한 운영 프로세스를 지원합니다. 사용 사례의 예는 [Airflow 및 dbt Core를 사용한 ELT](https://www.astronomer.io/docs/learn/use-case-airflow-dbt)를 참조하세요. 
- 비즈니스 운영: Airflow 사용자의 68%가 Airflow를 시용하여 비즈니스를 지원하는 데이터를 직접 오케스트레이션하고 데이터 기반 애플리케이션과 제품을 만들었으며, 종종 MLOps 파이프라인과 함께 사용하기도 합니다. 사용 사례의 예는 [로렐 알고리즘: 완벽한 시간 관리를 위한 MLOps, AI 그리고 Airflow](https://www.astronomer.io/events/webinars/the-laurel-algorithm-mlops-ai-and-airflow-for-perfect-timekeeping-video/) 웨비나를 시청하세요.
- MLOps: Airflow 사용자의 28%가 이미 Apache Airflow로 머신 러닝 작업(MLOps)을 오케스트레이션하고 있습니다. MLOps에 Airflow를 사용할 때의 모범 사례에 대한 개요는 [Airflow로 MLOps 파이프라인을 오케스트레이션하기 위한 모범 사례](https://www.astronomer.io/docs/learn/airflow-mlops)에서 확인할 수 있습니다. 최첨단 ML 도구가 포함된 복잡한 사용 사례에 대해서는 [Cohere 및 OpenSearch를 사용하여 MLOps 파이프라인에서](https://www.astronomer.io/docs/learn/use-case-llm-customer-feedback) 고객 피드백 분석하기를 참조하세요.
- 인프라 관리: Airflow를 사용하여 인프라를 스핀업 및 스핀다운할 수 있습니다. 예를 들어, 데이터베이스에서 임시 테이블을 생성 및 삭제하거나 Spark 클러스터를 스핀업 및 스핀다운하는 데 사용할 수 있습니다. MLOps 파이프라인 사용 사례에서 [Airflow 설정/해체를 사용하여 데이터 품질 검사 실행하기](https://www.astronomer.io/docs/learn/use-case-setup-teardown-data-quality)에서는 이 기능을 데이터 품질 검사와 결합하는 방법을 보여 줍니다.


물론 이는 몇 가지 예시에 불과하며, Airflow로 거의 모든 종류의 배치 워크플로우를 오케스트레이션할 수 있습니다.

# Airflow 실행하기
Airflow를 실행하는 방법에는 여러 가지가 있스며, 그 중 일부는 다른 방법보다 쉽습니다. Astronomer이 추천하는 방법은 다음과 같습니다:

- 오픈 소스 [Astro CLI](https://www.astronomer.io/docs/astro/cli/get-started-cli)를 사용하여 로컬에서 Airflow를 실행하세요. Astro CLI는 [Docker](https://www.docker.com/)에서 실행되는 로컬 Airflow 인스턴스를 만드는 가장 쉬운 방법이며 누구나 무료로 사용할 수 있습니다.

- [Astro](https://astronomer.io/try-astro?utm_medium=docs&utm_content=-docs-learn-intro-to-airflo&utm_source=body)를 사용하여 프로덕션에서 Airflow 실행하기. Astro는 데이터 오케스트레이션을 위한 완전 관리형 SaaS 어플리케이션으로, 팀이 규모와 관계없이 Apache Airflow로 데이터 파이프라인을 작성하고 실행할 수 있도록 도와줍니다. [무료 평가판](https://astronomer.io/try-astro?utm_medium=docs&utm_content=-docs-learn-intro-to-airflo&utm_source=body)을 사용할 수 있습니다.

모든 Airflow 설치에는 webserver, scheduler, database 및 executor 등 필수 Airflow 구성 요소가 인프라의 일부로 포함되어 있습니다. 자세한 내용은 [Airflow 구성요소](https://www.astronomer.io/docs/learn/airflow-components)를 참조하세요.

# Airflow 개념
Airflow 리소스를 탐색하려면 다음의 Airflow 개념을 전반적으로 이해하는 것이 도움이 됩니다.

## Pipeline Basics
- DAG: Directed Acyclic Graph. Airflow DAG는 그래프로 정의된 워크플로우로, 노드 간의 모든 종속성이 직접적이고 노드가 자체 참조하지 않으므로 순환 종속성이 없습니다. Airflow DAG에 대한 자세한 내용은 [Airflow DAG 소개](https://www.astronomer.io/docs/learn/dags)를 참조하세요.
- DAG run: 특정 시점에 DAG를 실행합니다. DAG run은 다음의 네 가지 유형 중 하나일 수 있습니다: `scheduled`, `manual`, `dataset_trigger`, `backfill`.
- Task: 단일 작업 단위를 설명하는 DAG의 단계입니다.
- Task instance: 특정 시점의 작업 실행을 나타냅니다.
- Dynamic task: 런타임에 생성된 가변적인 수를 동적으로 매핑된 작업에 대한 청사진 역할을 하는 Airflow 작업입니다. 자세한 내용은 [Dynamic Task](https://www.astronomer.io/docs/learn/dynamic-tasks)를 참조하세요.

다음 스크린샷은 `get_astronauts`와 `print_astronaut_craft`라는 두 개의 태스크가 있는 `example_astornauts`라는 간단한 DAG를 보여줍니다. `get_astronauts` 작업은 일반 task이고 `print_astronaut_carft` 작업은 dynamic task입니다. Airflow UI의 그리드 뷰에는 개별 DAG 실행 및 작업 인스턴스가 표시되고 그래프에는 DAG의 구조가 표시됩니다. Airflow UI에 대한 자세한 내용은 [Airflow UI 소개](https://www.astronomer.io/docs/learn/airflow-ui)에서 배울 수 있습니다.

![Airflow Pipeline Basic](https://www.astronomer.io/docs/assets/images/intro-to-airflow_core_concepts_ui-90adff61a20c280f5a84f94bd28186c6.png)


<detail>
<summary>스크린샷에 사용된 전체 DAG 코드를 보려면 클릭하세요.</summary>
	
```python
"""
## Astronaut ETL example DAG

This DAG queries the list of astronauts currently in space from the 
Open Notify API and prints each astronaut's name and flying craft.
There are two tasks, one to get the data from the API and save the results,
and another to print the results. Both tasks are written in Python using
Airflow's TaskFlow API, which allows you to easily turn Python functions into
Airflow tasks, and automatically infer dependencies and pass data.

The second task uses dynamic task mapping to create a copy of the task for
each Astronaut in the list retrieved from the API. This list will change
depending on how many Astronauts are in space, and the DAG will adjust 
accordingly each time it runs.

For more explanation and getting started instructions, see our Write your 
first DAG tutorial: https://www.astronomer.io/docs/learn/get-started-with-airflow

![Picture of the ISS](https://www.esa.int/var/esa/storage/images/esa_multimedia/images/2010/02/space_station_over_earth/10293696-3-eng-GB/Space_Station_over_Earth_card_full.jpg)
"""

from airflow import Dataset
from airflow.decorators import dag, task
from pendulum import datetime
import requests


# Define the basic parameters of the DAG, like schedule and start_date
@dag(
    start_date=datetime(2024, 1, 1),
    schedule="@daily",
    catchup=False,
    doc_md=__doc__,
    default_args={"owner": "Astro", "retries": 3},
    tags=["example"],
)
def example_astronauts():
    # Define tasks
    @task(
        outlets=[Dataset("current_astronauts")]
    )  # Define that this task updates the `current_astronauts` Dataset
    def get_astronauts(**context) -> list[dict]:
        """
        This task uses the requests library to retrieve a list of Astronauts
        currently in space. The results are pushed to XCom with a specific key
        so they can be used in a downstream pipeline. The task returns a list
        of Astronauts to be used in the next task.
        """
        r = requests.get("http://api.open-notify.org/astros.json")
        number_of_people_in_space = r.json()["number"]
        list_of_people_in_space = r.json()["people"]

        context["ti"].xcom_push(
            key="number_of_people_in_space", value=number_of_people_in_space
        )
        return list_of_people_in_space

    @task
    def print_astronaut_craft(greeting: str, person_in_space: dict) -> None:
        """
        This task creates a print statement with the name of an
        Astronaut in space and the craft they are flying on from
        the API request results of the previous task, along with a
        greeting which is hard-coded in this example.
        """
        craft = person_in_space["craft"]
        name = person_in_space["name"]

        print(f"{name} is currently in space flying on the {craft}! {greeting}")

    # Use dynamic task mapping to run the print_astronaut_craft task for each
    # Astronaut in space
    print_astronaut_craft.partial(greeting="Hello! :)").expand(
        person_in_space=get_astronauts()  # Define dependencies using TaskFlow API syntax
    )


# Instantiate the DAG
example_astronauts()
```
</detail>

task를 가능한 작게 유지하는 것이 핵심 모범 사례입니다. 즉, 각 작업은 단일 작업을 수행합니다. 또한 작업은 멱등적이므로 동일한 입력으로 실행할 때마다 동일한 출력을 생성합니다. [Apache Airflow에서 DAG 작성 모범사례](https://www.astronomer.io/docs/learn/dag-best-practices)를 참조하세요.


## Pipeline 작성하기
Airflow tasks는 Python 코드로 정의됩니다. 다음을 사용하여 tasks를 정의할 수 있습니다:
- Decorators (@task): [TaskFlow API](https://www.astronomer.io/docs/learn/airflow-decorators)를 사용하면 Python 함수를 감싸는 Decorator 집합을 사용하여 작업을 정의할 수 있습니다. 이러한 작업은 기존 Python 스크립트에서 작업을 만드는 가장 쉬운 방식입니다. 데코레이션된 함수에 대한 각 호출은 DAG에서의 하나의 task가 됩니다.
- Operators (XYZOperator): [Operator](https://www.astronomer.io/docs/learn/what-is-an-operator)는 특정 작업을 수행하도록 설계된 파이썬 코드를 추상화한 클래스입니다. 클래스에 필요한 매개변수를 제공하여 Operator를 인스턴스화할 수 있습니다. 인스턴스화된 각 Operator는 DAG에서의 하나의 task가 됩니다.

언급할 가치가 있는 몇 가지 특별한 유형의 연산자가 있습니다:
- Sensor: [Sensor](https://www.astronomer.io/docs/learn/what-is-a-sensor)는 특정 조건이 충족될 때까지 계속 실행되는 Operator입니다. 예를 들어, [HttpSensor](https://registry.astronomer.io/providers/apache-airflow-providers-http/versions/latest/modules/HttpSensor)는 사용자가 정의한 조건 집합이 충족될 때까지 HTTP 요청을 기다립니다.

- Deferrable Operators: [Deferrable Operator](https://www.astronomer.io/docs/learn/deferrable-operators)는 파이썬 [비동기](https://docs.python.org/3/library/asyncio.html) 라이브러리를 사용하여 task를 비동기적으로 실행합니다. 예를 들어 [DateTimeSensorAsync](https://registry.astronomer.io/providers/astronomer-providers/modules/HttpOperatorAsync)는 특정 날짜와 시간이 되기 전까지 비동기적으로 기다립니다. Deferrable Operator를 사용하려면 Airflow 환경에서 triggerer component를 실행해야 한다는 것을 유의해야합니다.

BashOperator, `@task` decorator 또는 PythonOperator와 같이 일반적으로 사용되는 일부 빌딩 블록은 핵심 Airflow의 일부이며 모든 Airflow 인스턴스에 자동으로 설치됩니다. 또한 많은 Operator는 특정 서비스와 상호 작용하는 모듈을 패키지로 그룹화하는 **Airflow provider packages**에서 Airflow와 별도로 유지 관리됩니다.

[Astronomer Registry](https://registry.astronomer.io/)에서 사용 가능한 모든 연산자를 검색하고 해당 매개변수에 대한 자세한 설명을 찾을 수 있습니다. 일반적인 많은 데이터 도구의 경우, provider package의 간단한 구현을 보여주는 [통합 튜토리얼](https://www.astronomer.io/docs/learn/category/integrations--connections)을 이용가능합니다.


## 추가 개념
Airflow에는 DAG와 작업 외에도 훨씬 더 많은 것이 있지만, 다음은 여러분이 접할 수 있는 몇 가지 추가 개념과 기능입니다:
- Airflow scheduling: Airflow는 DAG를 스케줄링하는 다양한 방법을 제공합니다. 자세한 내용은 [Airflow의 DAG 스케줄링 및 타임테이블](https://www.astronomer.io/docs/learn/scheduling-in-airflow)을 참조하세요.
- Airflow connections: Airflow connections는 외부 시스템에 대한 자격 증명 및 기타 연결 정보를 저장하고 DAG에서 참조할 수 있는 방법을 제공합니다. 자세한 내용은 [Apache Airflow에서 연결 관리하기](https://www.astronomer.io/docs/learn/connections)를 참조하세요.
- Airflow variables: Airflow variables는 Airflow환경에 정보를 저장하는데 사용할 수 있는 key-value 쌍입니다. 자세한 내용은 [Airflow variables 사용하기](https://www.astronomer.io/docs/learn/airflow-variables)를 참조하세요.
- XComs: XComs는 교차 통신의 줄임말로, XCom을 사용하여 Airflow 작업 간에 정보를 전달할 수 있습니다. 자세한 내용은 [tasks간 데이터 전달하기](https://www.astronomer.io/docs/learn/airflow-passing-data-between-tasks)를 참조하세요.
- Airflow REST API: [Airflow REST API](https://airflow.apache.org/docs/apache-airflow/stable/stable-rest-api-ref.html)를 사용하면 Airflow가 RESTful 웹 서비스와 상호 작용할 수 있습니다.


# 리소스
- [Astronomer Webinars](https://www.astronomer.io/events/webinars/): Airflow and Astronomer 주제에 대한 라이브 심층 분석, 이전의 모든 웨비나는 온디멘드로 시청할 수 있습니다.
- [Astronomer Academy](https://academy.astronomer.io/): Airflow and Astronomer 주제에 대한 심층적인 비디오 강좌.
- [Official Airflow Documentation](https://airflow.apache.org/docs/): Apache Airflow의 공식 문서입니다..
- [Airflow GitHub](https://github.com/apache/airflow): Apache Airflow의 공식 깃허브 레포지토리.
- [Airflow Slack](https://apache-airflow-slack.herokuapp.com/): Airflow 관련 질문을 할 수 있는 최고의 장소인 공식 슬랙 워크스페이스.

# 다음 단계
이제 Apache Airflow에 대한 기본적인 이해를 마쳤으니, [Apache Airflow 시작하기](https://www.astronomer.io/docs/learn/get-started-with-airflow) 튜토리얼을 따라 첫 번째 DAG를 작성할 준비가 되었습니다.