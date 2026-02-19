# {{ .Title }}

{{ .RawContent }}
## Pages

{{ range .Pages }}
{{- $md := .OutputFormats.Get "markdown" }}
- [{{ .Title }}]({{ with $md }}{{ .RelPermalink }}{{ end }})
{{- end }}
