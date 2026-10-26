name: Build AAB

on:
  push:
    branches: [ "main" ]
  workflow_dispatch:

jobs:
  build:
    runs-on: ubuntu-latest

    steps:
    - name: Checkout repository
      uses: actions/checkout@v4

    - name: Unzip source code
      run: |
        unzip -q source.zip

    - name: Set up JDK 17
      uses: actions/setup-java@v4
      with:
        java-version: '17'
        distribution: 'temurin'

    - name: Setup Gradle
      uses: gradle/actions/setup-gradle@v3

    - name: Build Release AAB
      run: |
        cd English_Word_Trainer_2000_Arabic-2000
        gradle bundleRelease

    - name: Upload AAB
      uses: actions/upload-artifact@v4
      with:
        name: EnglishWordTrainer-AAB
        path: English_Word_Trainer_2000_Arabic-2000/app/build/outputs/bundle/release/*.aab
