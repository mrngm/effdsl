# Match Bool Prefix Query

A match bool prefix query analyzes its input and constructs a bool query from the terms. Each term except the last is used in a term query, and the last term is used in a prefix query.

### Example

```go
import (
	"github.com/sdqri/effdsl"
	mbpq "github.com/sdqri/effdsl/queries/matchboolprefix"
)

query, err := effdsl.Define(
    mbpq.MatchBoolPrefixQuery(
        "message",
        "quick brown f",
        mbpq.WithAnalyzer("keyword"),
    )
)

res, err := es.Search(
    es.Search.WithBody(strings.NewReader(query)),
)
```

### Parameters

* **Field string**  
    The field you wish to search. This is a required parameter.

* **Query string**  
    The query text you wish to search for in the provided field. This is a required parameter.

* **WithAnalyzer(string)**  
    Analyzer used to convert the text in the query value into tokens. If no analyzer is provided, the default analyzer for the field is used.

### Additional Information

For more details on the match bool prefix query and its parameters, refer to the [official Elasticsearch documentation on match bool prefix queries](https://www.elastic.co/guide/en/elasticsearch/reference/current/query-dsl-match-bool-prefix-query.html).
