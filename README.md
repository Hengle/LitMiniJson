# LitMiniJson
Re-encapsulate LitJson for supporting iOS. Replace the module of parsing with MiniJson.

Features:
1. The Same API with LitJson.
2. Support iOS/Android/WP8/Win8.
3. Stable and good performance.

Sample:
There is a string named 'str' with contents as below:
{
    "status":0,
    "msg":"ok",
    "data":
    {
        "friends":
        [
            {"id":1, "name":"night"},
            {"id":3, "name":"tom"}
        ]
    }
}

using LitJson;

// string --> json object
JsonData contentData = JsonMapper.ToObject(str);
JsonData friendsData = contentData["data"]["friends"];
for (int i = 0; i < friendsData.Count; i++) {
    int id = int.Parse(friendsData[i]["id"].ToString()); // 1 or 3
    string name = friendsData[i]["name"].ToString();     // night or tom
}

// json object --> string
string strFriends = friendsData.ToJson(); // strFriends is "[{\"id\":1, \"name\":\"night\"},{\"id\":3, \"name\":\"tom\"}]"

// create or modify json object
JsonData newFriend = new JsonData();
newFriend["id"] = 4;
newFriend["name"] = "terry";
friendsData.Add(newFriend);
strFriends = friendsData.ToJson(); // strFriends is "[{\"id\":1, \"name\":\"night\"},{\"id\":3, \"name\":\"tom\"},{\"id\":4, \"name\":\"terry\"}]"
=============================================


����˵��:
LitJson��Ϊʹ���˷��䣬��֧��iOSƽ̨�������Ұѽ���ģ���滻����MiniJson��

���ԣ�
1. �ӿڸ�LitJson��ȫһ�¡�
2. ֧��iOS/Android/WP8/Win8��ƽ̨��
3. ���϶����Ϸ�����ȶ����У��ɿ��Ժ�������ȫû���⡣
