# Seraph Hack Build

This repository contains build automation for the Seraph Hack Minecraft mod project.

## Project Structure

```
repository/
├── seraphhack-1.2.0.zip     # Source archive
├── .github/workflows/
│   └── build.yml            # CI/CD workflow
└── README.md                # This file
```

## Build Process

### Automated Build (GitHub Actions)

1. Go to **Actions** tab
2. Select **Build Seraph Hack** workflow
3. Click **Run workflow** button
4. The workflow will:
   - Extract `seraphhack-1.2.0.zip`
   - Detect the Gradle project
   - Create Gradle wrapper (if needed)
   - Build the mod
   - Upload artifacts

### Local Build

If you have the extracted Gradle project:

```bash
cd project/path/to/gradle/project
chmod +x gradlew
./gradlew clean build
```

## Workflow Steps Explained

1. **Checkout** - Clone the repository
2. **Setup Java 21** - Install Java using Temurin
3. **Extract Archive** - Unzip the Seraph Hack source
4. **Locate Project** - Find the Gradle project directory
5. **Setup Gradle** - Install Gradle 8.8
6. **Create Wrapper** - Generate gradle wrapper scripts
7. **Build** - Run `./gradlew clean build`
8. **Upload** - Publish built JAR files as artifacts

## Troubleshooting

### Build fails with "gradlew not found"

The workflow now automatically creates the Gradle wrapper. If it still fails:

```bash
gradle wrapper --gradle-version 8.8
```

### No JAR files in build/libs

Check that:
- The extracted project has a valid `build.gradle` or `build.gradle.kts`
- Java 21 is properly set up
- No compilation errors in the source code

### Need to debug?

The workflow includes `--info` flag for detailed Gradle output. Check the full logs in GitHub Actions.

## Requirements

- Java 21
- Gradle 8.8 (handled by wrapper)

## License

See the Seraph Hack project license in the extracted archive.
