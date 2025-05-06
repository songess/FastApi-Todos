# Python 3.9 베이스 이미지 사용
FROM python:3.9

# 비특권 사용자 생성
RUN useradd -m -u 1000 appuser

# 작업 디렉토리 설정
WORKDIR /app

# 필요한 파일 복사
COPY requirements.txt .
COPY main.py .
COPY todo.json .
COPY static/ ./static/
COPY templates/ ./templates/
COPY tests/ ./tests/

# 의존성 설치
RUN pip install --no-cache-dir -r requirements.txt

# 파일 소유권 변경
RUN chown -R appuser:appuser /app

# 비특권 사용자로 전환
USER appuser

# FastAPI 서버 실행
CMD ["uvicorn", "main:app", "--host", "0.0.0.0", "--port", "5001"]