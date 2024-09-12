# Airflow 퀵스타트

Airflow의 기능과 사용 사례를 알아보는 가장 좋은 방법은 Astronomer의 [Airflow](https://github.com/astronomer/airflow-quickstart) 퀵스타트를 사용하는 것입니다.

이 퀵스타트는 Airflow, [DuckDB](https://duckdb.org/), [Streamlit](https://streamlit.io/), [Astro Python SDK](https://astro-sdk-python.readthedocs.io/en/stable/index.html) 등의 오픈 소스 도구를 사용하여 시간에 따른 전 세계 및 지역 온도 변화를 보여주는 대화형 대시보드를 생성하는 ELT 파이프라인을 구현합니다.

![Quickstart](https://www.astronomer.io/docs/assets/images/quickstart_streamlit_result_1-11f98b8db76ad48616ad9a078c8c9410.png)


[GitHub Codespaces](https://github.com/features/codespaces)를 사용하면 로컬에 아무것도 설치하지 않고도 빠른 시작을 실행할 수 있고, [Astro CLI](https://www.astronomer.io/docs/astro/cli/install-cli)를 사용하여 로컬에서 실행할 수도 있습니다.

이 프로젝트는 Airflow가 무엇을 할 수 있는지 보여주고 중요한 Airflow 개념을 탐색할 수 있는 샌드박스를 제공하도록 설계되었습니다. 레포지토리에는 사용자 코드 변경 없이 대화형 대시보드를 만들고 채울 수 있는 미리 빌드된 파이프라인 하나와 완료되면 대시보드를 개선할 수 있는 몇 가지 연습이 포함되어 있습니다. 퀵스타트에 대한 자세한 지침은 [프로젝트 Readme](https://github.com/astronomer/airflow-quickstart/blob/main/README.md)를 참조하세요.


💡TIP
Airflow를 처음 사용하시는 분이라면 시작하기 위한 자세한 지침이 필요하시다면 [Airflow 시작하기 튜토리얼](https://www.astronomer.io/docs/learn/get-started-with-airflow)을 단계별로 살펴보세요.

## 다루는 개념

이 퀵스타트의 사전 구축된 파이프라인과 연습은 몇 가지 주요 Airflow 기능의 구현을 보여 주며, 자세한 내용은 학습 리소스에서 확인할 수 있습니다:

- [Datasets](https://www.astronomer.io/docs/learn/airflow-datasets): 이 기능은 Airflow가 데이터를 인식하고 Airflow 스케줄링 기능을 확장하는 데 도움이 됩니다. Datasets를 사용하여 공유 데이터를 업데이트하는 다른 작업이 완료된 경우에만 DAG가 실행되도록 예약할 수 있습니다.
- [Dynamic task mapping](https://www.astronomer.io/docs/learn/dynamic-tasks): 이 기능을 사용하면 이전 작업이나 외부 기준에 띠리 런타임에 병렬 작업을 동적으로 생성하는 DAG를 작성할 수 있습니다.
- [Astro Python SDK](https://www.astronomer.io/docs/learn/astro-python-sdk) : Airflow를 기반으로 구축된 이 오픈 소스 패키지는 파일 로드나 SQL 또는 Pandas를 사용한 데이터 변환과 같은 일반적인 ELT 작업을 간소화하는 함수와 클래스를 제공합니다.