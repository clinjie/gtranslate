# gtranslate ![build](https://travis-ci.com/bregydoc/gtranslate.svg?branch=master)

Google Translate API for unlimited and free translations 📢.
This project was inspired by [google-translate-api](https://github.com/matheuss/google-translate-api) and [google-translate-token](https://github.com/matheuss/google-translate-token).

# Install

    go get github.com/bregydoc/gtranslate

# Use

```go
gtranslate.LangDetect("I'm alive", 0, 1)
```

```go
gtranslate.Translate("I'm alive", language.English, language.Spanish)
```

```go
gtranslate.TranslateWithParams("I'm alive", gtranslate.TranslateWithParams{From: "en", To: "es"})
```

```go
gtranslate.TranslatePure("I'm alive", "en", "es")
```

# Example

```go
package main

import (
   "fmt"

	"github.com/clinjie/gtranslate"
)

func main() {
	text := "you are so green."
   
   detectLanguage, confidence, err := gtranslate.LangDetect(text, 0, 1)
   
	if err != nil {
		panic(err)
	}

	fmt.Printf("source text is: %s | detect language is: %s | detect language conf is: %f\n", 
				text, detectLanguage, confidence)

	translateText, err := gtranslate.TranslatePure(text, "en", "zh")

	if err != nil {
		panic(err)
	}

	fmt.Printf("source text is: %s | translate text is: %s\n", 
				text, translateText)
}
```
