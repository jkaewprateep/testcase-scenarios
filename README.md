# testcase-scenarios
Test case with application scenarios

<p align="center" width="100%">
    <img width="25%" src="https://github.com/jkaewprateep/Python_and_CURL/blob/main/Python.jpg">
    <img width="22%" src="https://github.com/jkaewprateep/testcase-scenarios/blob/main/Curl_command.jpg">
    <img width="5.84%" src="https://github.com/jkaewprateep/testcase-scenarios/blob/main/image7.jpg">
    <img width="10.5%" src="https://github.com/jkaewprateep/testcase-scenarios/blob/main/kid_41.png"> </br> 
    <b> Perform test scenarios with Python scripts and CURL command </b> </br>
    <b> ( Picture from Internet ) </b> </br>
</p>

🧸💬 It is user-controllable and useful if a user can develop and analyze their test scripts, Python language can be directly modified and run as user requirements, traceable and repeatable with user requirements methods. </br> 
👧💬 🎈 Certification and secured communication can apply even in script language you can modify the path of the certificate CA file at ```verify=c:\dekdee..crt``` for requests method and ```--cacert c:\dekdee.crt``` of the CURL command. </br>
🐑💬 ➰ Secured does not mean unbreakable but will find difficult to break, some communication creates sessions with randoms secrete found at the time or terminals and complete communication fast enough until tracing and repeatable cannot break the secrete then allowed to perform ```fast algorithms``` the Basic authentication without secrete code is one of the fast algorithms. </br>


## Simple test case method for scenarios ##

🦭💬 By application design back-end and front-end interfaces with RESTful web services API frontier, controllable with standard message communication method that creates communication path, negotiation for web-sockets, or exchange information over reachable networks. This method performs tests by two levels of ```Python requests``` method and curl command because the requests are required to read website information once before passing website communication negotiation requirements to CURL commands that include ```CORS message exchange origin``` and other parameters. </br>
🐐💬 In some scenarios we required first-time negotiation for website attributes requirements and you may find ```401 - unauthoriazatoin``` one message before the ```200 - OK``` response, ```201 - create``` response, or another message in the communication path. This technique is called ```least requirements``` is a famous method to guarantee the communication path of multiple application access requirements and make it short by one-time testing or ```attribute assertion requirements```. </br>

```
def request_getinaccountinfo ():
    
    url = "https://localhost:8080/getAccount";
    payload = "";
    target_header = ["accept"];
    headers = { "accept":"application/json" };

    r = requests.get(url, data=json.dumps(payload), headers=headers, verify=False)
    r.headers = dict(['"{0}: {1}"'.format(k, v) for k, v in r.headers.items() if k in target_header]);
    req = r.request;

    command = "curl -k -X GET";
    method = req.method;
    uri = req.url;
    data = req.body;

    headers = ['"{0}: {1}"'.format(k, v) for k, v in req.headers.items() if k in target_header];
    headers = " -H " + " -H ".join(headers);
    command_tosend = command.format(method=method, headers=headers, data=data, uri=uri);
    command_tosend = command_tosend + headers + " " + uri + ' --user "' + username + ":" + password + '"';

    print( command_tosend )

    args = shlex.split(command_tosend);
    process = subprocess.Popen(args, shell=False, stdout=subprocess.PIPE, stderr=subprocess.PIPE)
    stdout, stderr = process.communicate();

    result = ast.literal_eval(stdout.decode('utf-8'))

    process.stdout.close();
    
    return result.get("cash");
```

## Test scenarios ##

🐯💬 Culture-INFO, test scenarios, more than documents, flat files, and spreadsheets, the scripts find and readme.file must indicate the step tasks running for the benefit of the organization. An example of data output helps to save time for analysis and where should it be kept is where it is easy to find when it is requirements. <br>
🦁💬 Submitting tasks requires log analysis and test cases because repeating tasks is the first step of analysis and it saves time for auditing, testing, debugging from tracing logs, repeating issues, and analysis and user requirements. Good test scenarios and tracing help to save time in work scenarios not only development time but also auditing time. <br>

```
for i in range(1, 1001, 1):
    
    """""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""
    4. Read active list
    """""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""
    # listof_assets = request_getactiveasset ();
    # print( listof_assets )

    selected_asset = select_oneasset( [] );
    asset_id = selected_asset[1];
    asset_name = selected_asset[0];
    amount = select_amont(4) + 1;
    payload = dict({ });
    
    # print("amount: ", amount);

    """""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""
    5. Create buy order
    """""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""
    result = request_createbuyorder( asset_id, amount, payload );
    print('"""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""');
    print(result);
    # print(result.keys())
    print('"""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""');
    # {'id': '3d3f346f-d8ff-4bed-b428-4394d80a9192', 'client_order_id': '54f08119-1731-4d6e-8156-d335da3ba0b1', 'created_at': '2024-12-02T11:52:00.872117999Z', 'updated_at': '2024-12-02T11:52:00.876536058Z', 'submitted_at': '2024-12-02T11:52:00.872117999Z', 'filled_at': None, 'expired_at': None, 'canceled_at': None, 'failed_at': None, 'replaced_at': None, 'replaced_by': None, 'replaces': None, 'asset_id': 'bb2a26c0-4c77-4801-8afc-82e8142ac7b8', 'symbol': 'NFLX', 'asset_class': 'us_equity', 'notional': None, 'qty': '2', 'filled_qty': '0', 'filled_avg_price': None, 'order_class': '', 'order_type': 'market', 'type': 'market', 'side': 'buy', 'position_intent': 'buy_to_open', 'time_in_force': 'gtc', 'limit_price': None, 'stop_price': None, 'status': 'pending_new', 'extended_hours': False, 'legs': None, 'trail_percent': None, 'trail_price': None, 'hwm': None, 'subtag': None, 'source': None, 'expires_at': '2025-02-28T21:00:00Z'}
    
    if "message" not in result.keys() and "id" in result.keys() :
        listof_orders.append([ result["id"], result["symbol"], result["qty"], result["time_in_force"] ])
    # [['520c2fdb-93b3-4024-9f42-7c48ffeec846', 'NFLX', '2', 'gtc']]

    """""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""
    6. Get all closed orders
    """""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""
    result = request_getallorders ();
    for item in result :
        if isinstance(item, dict) :
            if item["side"] == "buy" :
                if item["order_type"] == "market" : 
                    if item["status"] not in ["filled"] : 
                        listof_closedorders.append([ item["id"], item["symbol"], item["asset_id"], item["status"], item["qty"] ])

    # print( listof_closedorders );
    # [['ad919c10-82e5-4d07-b8fd-83856644e26c', 'NVNIW', '9a33a489-3d15-46c5-8ece-3d74193e4b03', 'filled', '1'], ['997365dc-4af1-45c3-a76b-c2ce4720f4b0', 'NVNIW', '9a33a489-3d15-46c5-8ece-3d74193e4b03', 'filled', '1'], ['3c4df78e-b64c-4988-9ae8-4f592c90163a', 'NVNIW', '9a33a489-3d15-46c5-8ece-3d74193e4b03', 'filled', '1'], ['ac250aa0-942e-4d34-b2d8-8d145079863d', 'NVNIW', '9a33a489-3d15-46c5-8ece-3d74193e4b03', 'replaced', '1'], ['9d600498-258c-4492-9964-048735ca3850', 'NVNIW', '9a33a489-3d15-46c5-8ece-3d74193e4b03', 'replaced', '1'], ['ac5864a3-eb2f-46b6-8cc0-7c9668a6f057', 'CETY', 'a517246f-3646-45ce-be31-c7702786dfc9', 'replaced', '1']]

    """""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""
    7. Random seleted from order list return
    """""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""
    index = select_amont( len(listof_closedorders) );
    # print("index: ", index)
    if len(listof_closedorders) > 0 :
        target = listof_closedorders[index - 1];
        
        # print(">>>>")
        # print(target[1])
        # print(">>>>")
        
        result = robin_stocks.robinhood.stocks.get_quotes(target[1])[0];
      
        if result != None :
            if "ask_price" in result.keys():
                print('"""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""');
                print( target[1], ":", result["ask_price"], "amount:", amount )
                print('"""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""');

        # ['997365dc-4af1-45c3-a76b-c2ce4720f4b0', 'NVNIW', '9a33a489-3d15-46c5-8ece-3d74193e4b03', 'filled', '1']

        """""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""
        8. Create sell order
        """""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""
        result = request_createsellorder( target[2], target[4], payload );
        print('"""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""');
        print(result);
        print('"""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""');
        # print(result, maximum_qty, _temp);
        # {'code': 40310000, 'existing_order_id': '1bd5fa88-d2f4-4de3-872b-0b34b11550d9', 'message': 'potential wash trade detected. use complex orders', 'reject_reason': 'opposite side market/stop order exists'}
    
    time.sleep(15);
    
    # cash = request_getinaccountinfo ();
    cash = request_getrobotinfo();
    print('"""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""');
    print( "cash: ", cash );
    print('"""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""');
    
    if i == 999 :
        i = 1;
```

---

<p align="center" width="100%">
    <img width="30%" src="https://github.com/jkaewprateep/advanced_mysql_topics_notes/blob/main/custom_dataset.png">
    <img width="30%" src="https://github.com/jkaewprateep/advanced_mysql_topics_notes/blob/main/custom_dataset_2.png"> </br>
    <b> 🥺💬 รับจ้างเขียน functions </b> </br>
</p
