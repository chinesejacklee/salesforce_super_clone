Salesforce's record clone function only clones the record itself without taking into the account of its "detail/child" records. The Super Clone provides both API (can be directly called from your own code) and visual force page UI access to clone the master and detail records in one go. An example of API access:

//clone an account record (id is a0190000001E3JJ) with all related detail records(contact,opportunity...) //note, detailed records to be cloned can be further declared. By default, it takes all child records.

Clone cc=new Clone(); string parentObjAPIName=cc.returnAPIObjectName('a0190000001E3JJ'); Map<string,string> objLabelobjAPI=cc.getAllChildObjNames(parentObjAPIName,'a0190000001E3JJ'); string clondedParentRecordID=cc.startsClone('a0190000001E3JJ', objLabelobjAPI.values());

That's it, totally 4 lines code.

To user vf page, all you need to do is to pass Salesforce master record id to the URL: yoursalesforce instance.salesforce.com/apex/clone?id=salesforce master record id, e.g:

https://ap1.visual.force.com/apex/clone?id=00190000004ZlVc
