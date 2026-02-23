# 🗂️ Portfolio

A personal portfolio website built with **Spring Boot** and **Thymeleaf**, featuring a contact form with email delivery. The site is fully containerised with Docker and can be deployed to any environment that supports Java 21.

---

## 🌐 Live Demo

> Add your live site URL here once deployed.
> Example: `https://your-portfolio.example.com`

---

## 📸 Preview

> Add a screenshot or screen-recording GIF of the running site here.
> Example:
> ```
> ![Portfolio preview](docs/preview.png)
> ```

---

## ✨ Features

- Responsive single-page layout with smooth-scroll navigation
- Dedicated sections: **Hero**, **About**, **Experience**, **Projects**, **Achievements**, and **Contact**
- Working contact form — messages are delivered directly to your inbox via Gmail SMTP
- Thymeleaf server-side templating with reusable HTML fragments
- Live-reload in development via Spring Boot DevTools
- Production-ready multi-stage **Dockerfile**

---

## 🛠️ Tech Stack

| Layer | Technology |
|-------|-----------|
| Language | Java 21 |
| Framework | Spring Boot 4.x |
| View layer | Thymeleaf |
| Web | Spring Web MVC |
| Mail | Spring Mail (Gmail SMTP) |
| Build | Apache Maven (Maven Wrapper) |
| Container | Docker (multi-stage build) |

---

## 🚀 Getting Started

### Prerequisites

- **Java 21** (JDK) — [Download](https://adoptium.net/)
- **Maven 3.9+** *or* use the included `./mvnw` / `mvnw.cmd` wrapper (no separate install required)
- **Docker** *(optional, for containerised deployment)*
- A Gmail account with an [App Password](https://support.google.com/accounts/answer/185833) configured for the contact form

### Installation

```bash
# 1. Clone the repository
git clone https://github.com/Shantanu106/Portfolio.git
cd Portfolio/portfolio

# 2. (Optional) Copy and edit the application properties
#    Set your own mail credentials before running
cp src/main/resources/application.properties src/main/resources/application-local.properties
```

### Configuration

Open `portfolio/src/main/resources/application.properties` and update the mail settings:

```properties
spring.mail.username=your-gmail@gmail.com
spring.mail.password=your-app-password
```

> ⚠️ **Never commit real credentials.** Use environment variables or a local properties file that is excluded from version control.

### Running Locally

```bash
# From the portfolio/ directory
./mvnw spring-boot:run
```

The application will start on **http://localhost:8080** by default.

To use a different port, set the `PORT` environment variable:

```bash
PORT=9090 ./mvnw spring-boot:run
```

### Running Tests

```bash
./mvnw test
```

---

## 📁 Project Structure

```
Portfolio/
└── portfolio/                  # Spring Boot application root
    ├── src/
    │   ├── main/
    │   │   ├── java/in/shantanu/portfolio/
    │   │   │   ├── PortfolioApplication.java   # Application entry point
    │   │   │   ├── controller/
    │   │   │   │   └── HomeController.java      # Request handling & routing
    │   │   │   ├── model/
    │   │   │   │   └── ContactRequest.java      # Contact form model
    │   │   │   └── service/
    │   │   │       └── EmailService.java        # Email delivery service
    │   │   └── resources/
    │   │       ├── application.properties       # App & mail configuration
    │   │       ├── static/                      # CSS, JS, images
    │   │       └── templates/                   # Thymeleaf templates
    │   │           ├── index.html               # Main page
    │   │           └── fragments/               # Reusable HTML sections
    │   └── test/                                # JUnit tests
    ├── Dockerfile                               # Multi-stage container build
    ├── mvnw / mvnw.cmd                          # Maven wrapper scripts
    └── pom.xml                                  # Project dependencies
```

---

## 🐳 Deployment

### Docker

```bash
# Build the image
cd portfolio
docker build -t portfolio:latest .

# Run the container
docker run -p 8080:8080 \
  -e SPRING_MAIL_USERNAME=your-gmail@gmail.com \
  -e SPRING_MAIL_PASSWORD=your-app-password \
  portfolio:latest
```

The application is exposed on port **8080** inside the container.

### Other Platforms

Because the application is packaged as a standard executable JAR, it can be deployed to any platform that supports Java 21, including:

- **Railway / Render / Fly.io** — point at the `Dockerfile` in `portfolio/`
- **AWS Elastic Beanstalk** — upload the JAR produced by `./mvnw package`
- **Heroku** — add a `Procfile` with `web: java -jar portfolio/target/*.jar`

---

## 🤝 Contributing

Contributions are welcome! Please follow these steps:

1. **Fork** the repository
2. Create a feature branch: `git checkout -b feature/your-feature`
3. Commit your changes: `git commit -m "feat: add your feature"`
4. Push to your fork: `git push origin feature/your-feature`
5. Open a **Pull Request** describing your changes

Please keep commits focused and write clear commit messages.

---

## 📄 License

This project does not currently include a license file. If you intend to share or reuse this code, consider adding an appropriate open-source license (e.g., [MIT](https://choosealicense.com/licenses/mit/)).

---

## 👤 Author

**Shantanu**

- GitHub: [@Shantanu106](https://github.com/Shantanu106)

---

> Built with ☕ Java and Spring Boot.
