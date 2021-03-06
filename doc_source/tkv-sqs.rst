.. Copyright 2010-2017 Amazon.com, Inc. or its affiliates. All Rights Reserved.

   This work is licensed under a Creative Commons Attribution-NonCommercial-ShareAlike 4.0
   International License (the "License"). You may not use this file except in compliance with the
   License. A copy of the License is located at http://creativecommons.org/licenses/by-nc-sa/4.0/.

   This file is distributed on an "AS IS" BASIS, WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND,
   either express or implied. See the License for the specific language governing permissions and
   limitations under the License.

.. _tkv-using-sqs:

##################################
Using |SQS| from AWS Explorer
##################################

.. meta::
   :description: Use Amazon SQS from AWS Explorer.
   :keywords: Amazon SQS, queue

|SQSlong| (|SQS|) is a flexible queue service that enables message passing between different
processes of execution in a software application. |SQS| queues are located in the AWS
infrastructure, but the processes that are passing messages can be located locally, on |EC2|
instances, or on some combination of these. |SQS| is ideal for coordinating the distribution of work
across multiple computers.

The |TVS| enables you to view |SQS| queues associated with the active account, create and delete
queues, and send messages through queues. (By active account, we mean the account selected in AWS
Explorer.)

For more information about |SQS|, go to :sqs-dg:`Introduction to SQS <IntroductionArticle>` in the AWS
documentation.

.. _tkv-sqs-create-queue:

Creating a Queue
================

You can create an |SQS| queue from AWS Explorer. The ARN and URL for the queue will be based on the
account number for the active account and the queue name you specify at creation.

*To create a queue*

1. In AWS Explorer, open the context (right-click) menu for the :guilabel:`Amazon SQS` node, and then
   choose :guilabel:`Create Queue`.

2. In the :guilabel:`Create Queue` dialog box, specify the queue name, the default visibility timeout,
   and the default delivery delay. The default visibility timeout and the default delivery delay
   are specified in seconds. The default visibility timeout is the amount of time that a message
   will be invisible to potential receiving processes after a given process has acquired the
   message. The default delivery delay is the amount of time from the moment the message is sent to
   the moment it first becomes visible to potential receiving processes.

3. Choose :guilabel:`OK`. The new queue will appear as a subnode under the :guilabel:`Amazon SQS` node.


.. _tkv-sqs-delete-queue:

Deleting a Queue
================

You can delete existing queues from AWS Explorer. If you delete a queue, any messages associated
with the queue are no longer available.

*To delete a queue*

1. In AWS Explorer, open the context (right-click) menus for the queue you want to delete, and then
   choose :guilabel:`Delete`.


.. _tkv-sqs-manage-queue:

Managing Queue Properties
=========================

You can view and edit the properties for any of the queues displayed in AWS Explorer. You can also
send messages to the queue from this properties view.

*To manage queue properties*

* In AWS Explorer, open the context (right-click) menu for the queue whose properties you want to
  manage, and then choose :guilabel:`View Queue`.

  From the queue properties view, you can edit the visibility timeout, the maximum message size,
  message retention period, and default delivery delay. The default delivery delay can be
  overridden when you send a message. In the following screenshot, the obscured text is the
  account number component of the queue ARN and URL.

.. figure:: images/tkv-sqs-queue-properties.png
   :scale: 85

   SQS queue properties view


.. _tkv-sqs-message-send:

Sending a Message to a Queue
============================

From the queue properties view, you can send a message to the queue.

*To send a message*

1. At the top of the queue properties view, choose the :guilabel:`Send` button.

2. Type the message. (Optional) Enter a delivery delay that will override the default delivery delay
   for the queue. In the following example, we have overridden the delay with a value of 240
   seconds. Choose :guilabel:`OK`.

   .. figure:: images/tkv-sqs-send-message.png
      :scale: 85

      :guilabel:`Send Message` dialog box

3. Wait for approximately 240 seconds (four minutes). The message will appear in the :guilabel:`Message
   Sampling` section of the of the queue properties view.

   .. figure:: images/tkv-sqs-message-sent.png
      :scale: 85

      SQS properties view with sent message

   The timestamp in the queue properties view is the time you chose the :guilabel:`Send` button. It
   does not include the delay. Therefore, the time that the message appears in the queue and is
   available to receivers might be later than this timestamp. The timestamp is displayed in your
   computer's local time.



