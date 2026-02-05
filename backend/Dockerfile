# 1단계: 빌드 (자바 코드를 실행 가능한 jar 파일로 만듦)
FROM eclipse-temurin:21-jdk-jammy AS build
WORKDIR /app
COPY . .
# 윈도우에서 작성한 실행 권한 문제를 해결하기 위해 추가
RUN chmod +x ./gradlew
RUN ./gradlew bootJar

# 2단계: 실행 (가벼운 환경에서 서버만 띄움)
FROM eclipse-temurin:21-jre-jammy
WORKDIR /app
COPY --from=build /app/build/libs/*.jar app.jar
EXPOSE 8080
ENTRYPOINT ["java", "-jar", "app.jar"]