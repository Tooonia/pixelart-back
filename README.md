# PixelArt API

This is a Spring Boot application for drawing and managing pixel art collections.

## Getting Started

Follow these instructions to set up and run the application locally.

### Prerequisites

* Java 11+
* Maven 3.6+
* PostgreSQL database (version 10 or higher recommended)
* Git

### Local Setup

1.  **Clone the repository:**
    ```bash
    git clone https://github.com/Tooonia/pixelart-back.git
    cd pixelart-back
    ```

2.  **Database Configuration:**
    This application requires a PostgreSQL database. Ensure you have a PostgreSQL instance running (e.g., via Docker, or a local installation).

    **Environment Variables for Database & Secrets:**
    The application relies on several environment variables for sensitive data and environment-specific configuration. These **must be set in your operating system's environment or in your IDE's run configuration**. **Do NOT hardcode these values in `application.properties` or commit them to Git.**

    | Variable Name       | Purpose                                                    | Example Value (for local dev)                           | Required | Notes                                                                                                                                                                                                         |
    | :------------------ | :--------------------------------------------------------- | :------------------------------------------------------ | :------- | :------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
    | `PORT`              | The port on which the Spring Boot application will run.    | `8085`                                                  | Optional | Defaults to `8085` if not set.                                                                                                                                                                                |
    | `DB_URL`            | The JDBC URL for the PostgreSQL database connection.       | `jdbc:postgresql://localhost:5432/pixelart_dev`         | Yes      | Use a separate database for development (e.g., `pixelart_dev`).                                                                                                                                               |
    | `DB_USERNAME`       | Username for the PostgreSQL database.                      | `pixelart_dev_user`                                     | Yes      | Ensure this user has appropriate permissions on the `pixelart_dev` database.                                                                                                                                  |
    | `DB_PASSWORD`       | Password for the PostgreSQL database user.                 | `your_secure_dev_password`                              | Yes      | **CRITICAL: Keep this secure.** Never commit to Git.                                                                                                                                                          |
    | `HIBERNATE_DDL_AUTO`| Controls Hibernate's schema update behavior.               | `update`                                                | Optional | For local development, `update` can be convenient for automatic schema generation. <br> For production, this should be `none` or `validate` to prevent accidental schema changes. Defaults to `none` if not set.   |
    | `JWT_SECRET_KEY`    | The secret key used for signing and verifying JWTs.        | `aVeryLongAndComplexSecretKeyThatIsAtLeast256BitsOrMore`| Yes      | **CRITICAL: This is highly sensitive.** Generate a strong, unique key. Never commit to Git.                                                                                                                   |

    **How to Set Environment Variables:**
    * **For permanent local setup (Linux/macOS):** Add `export VAR_NAME="value"` lines to your `~/.bashrc`, `~/.zshrc`, or `~/.profile` and then `source` the file.
    * **For permanent local setup (Windows):** Use `setx VAR_NAME "value"` in Command Prompt (restart terminal/IDE to take effect), or set them via the System Properties dialog.
    * **For IDE Run Configuration:** In IntelliJ IDEA/VS Code, configure the environment variables directly within your application's run/debug configuration settings.

3.  **Run the application:**
    ```bash
    ./mvnw spring-boot:run
    ```
    (Or run from your IDE).

---
