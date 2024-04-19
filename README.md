# LGPA 2022 ~ 2024 data crawing
### 프로젝트 기간 (2024-04-19 ~ )
### written by 류홍규

## 목적: LGPA 프로 선수들의 스탯을 분석하여 비교
### 기준점: Driving Accuracy
- Driving Accuracy Top선수들의 선수별 세부 Stats를 수집

### 선수들의 세부 Stats 수집 지표
| Category                |                        |
|-------------------------|------------------------|
| Average Driving Distance| 드라이빙 거리(파4홀과 파5홀 티샷친 평균거리)
| Driving Accuracy        | 드라이빙 정확도(파4, 파5홀에서 티샷을 페어웨이에 떨어진 것을 측정)
| Greens in Regulation    | 그린 적중률(티샷 후 그린에 공이 올라간 것)
| Putts Per GIR           | 퍼팅수 / 그린 적중률 (낮을 수록 좋은 것)
| Putting Average         | 평균 퍼팅 수
| Sand Saves              | 벙커에서 첫번째 샷 후 그린에 성공적으로 공을 놓을 확률
| Scoring Average         | 한 라운드(18홀)에서 평균적으로 치는 점수
| Rounds Under Par        | 파보다 낮은 점수로 라운드를 마친 횟수
| Total Rounds Played     | 선수가 대회중에 참여한 총 라운드 수

- eagle의 경우 잘 안 나오기도 하며, 일반인들은 eagle은 나오기가 힘드니 배제했다.
### 수집이 너무 오래 걸리는 현상 (해결)
```python
concurrent.futures.ThreadPoolExecutor
```
- I/O 바운드 작업에서 성능이 향상되며, 병렬 처리를 통해 기존 10분 이상에서 37초로 시간을 단축하였습니다.
- 다만, Python은 GIL(Global Interpreter Lock) 때문에 CPU-bound 작업의 병렬 처리에 한계가 있어, ProcessPoolExecutor를 사용하는 것도 좋은 방법이라 생각합니다.
- GIL은 한번에 하나의 스레드만 Python바이트코드를 실행할 수 있는 반면, 고성능 CPU에서는 ProcessPoolExecutor를 사용하면, 별도의 프로세스를 사용하여 병렬처리를 구현하기 때문에, 효과적으로 처리할 수 있기 때문입니다. 

![image](https://github.com/HongkyuRyu/portfolio/assets/69923886/02ee16cc-460a-401b-85ec-5d92e9bdeb7b)
