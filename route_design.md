POST /sort-names Route Design Recipe

1. Design the Route Signature
You'll need to include:
method: post
path: /sort-names
body parameters: names=Joe,Alice,Zoe,Julia,Kieran

2. Design the Response

<!-- Response when the post is found: 200 OK -->
Alice,Joe,Julia,Kieran,Zoe

3. Write Examples

# Request:

post /sort-names

# Expected response:

Alice,Joe,Julia,Kieran,Zoe

Response for 200 OK

4. Encode as Tests Examples
# EXAMPLE
# file: spec/integration/application_spec.rb

require "spec_helper"

describe Application do
  include Rack::Test::Methods

  let(:app) { Application.new }

  context 'POST /sort-names' do

    let(:names) { 'Joe,Alice,Zoe,Julia,Kieran' }

    it 'returns 200 OK with the correct body' do
      response = post("/sort-names", names: names)

      expect(response.status).to eq 200
      expect(response.body).to eq 'Alice,Joe,Julia,Kieran,Zoe'
    end
  end 
end
5. Implement the Route
Write the route and web server code to implement the route behaviour.