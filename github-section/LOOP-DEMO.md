# 연습 폴더와 리포
mkdir branch-demo
cd branch-demo
git init -b main

# A: 첫 커밋
echo "# TicketDrop" > README.md
git add README.md
git commit -m "A: README 추가"

# B
echo "class Event: pass" > models.py
git add models.py
git commit -m "B: Event 모델"

# C: 이미 추적 중인 파일이라 -a로 add까지
echo "class Seat: pass" >> models.py
git commit -am "C: Seat 모델"

# 오늘 작업 브랜치 (main의 최신 커밋 C에서)
git switch -c day06-seat-hold

# D
echo "def hold(seat_id): return True" > seat_service.py
git add seat_service.py
git commit -m "D: 좌석 홀드"
# 이름표가 가리키는 해시: 지금은 D
cat .git/refs/heads/day06-seat-hold

# E
echo "def test_hold(): assert True" > test_seat_service.py
git add test_seat_service.py
git commit -m "E: 홀드 테스트"
# 같은 파일을 다시 보면 해시가 E로 바뀌어 있다
cat .git/refs/heads/day06-seat-hold

# 그래프, main 이름표, HEAD
git log --oneline --graph --all
cat .git/refs/heads/main
cat .git/HEAD

# 브랜치를 바꾸면 HEAD가 main을 가리키고 인덱스와 작업 트리도 main 상태로 바뀐다
git switch main
cat .git/HEAD