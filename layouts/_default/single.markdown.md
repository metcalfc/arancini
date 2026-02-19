---
url: {{ .Permalink }}
{{- with .Date }}
date: {{ .Format "2006-01-02" }}
{{- end }}
{{- with .Params.author }}
author: {{ . }}
{{- end }}
{{- with .Description }}
description: {{ . }}
{{- end }}
{{- with .Params.tags }}
tags: [{{ delimit . ", " }}]
{{- end }}
---

# {{ .Title }}

{{ .RawContent }}
