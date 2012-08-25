# Go Twitter

This is a simple module to communicate with the Twitter API.

**Note:** This is library is currently very simple and only supports use of the
stream API.

## Installation

    go get github.com/blixt/go-twitter/twitter

## Examples

### Stream tweets in real time

    package main
    
    import (
    	"fmt"
    	"github.com/blixt/go-twitter/twitter"
    )
    
    func main() {
    	stream := &twitter.StreamApi{"username", "password"}
    
    	tweets := make(chan *twitter.Tweet)
    	go stream.StatusesFilter([]string{"hello"}, tweets)
    	for tweet := range tweets {
    		fmt.Printf("@%s: \"%s\"\n", tweet.User.ScreenName, tweet.Text)
    	}
    }
