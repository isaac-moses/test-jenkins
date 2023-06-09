def action = 'create' // Set the desired action: create, update, or delete
def channel = 'my-channel' // Set the channel name
def webhook = 'my-webhook' // Set the webhook value

def secretCommand

if (action == 'create') {
    secretCommand = 'add'
} else if (action == 'update') {
    secretCommand = 'update'
} else if (action == 'delete') {
    secretCommand = 'delete'
} else {
    error("Invalid action: ${action}")
}

println("Action: ${action}")
println("Channel: ${channel}")
println("Webhook: ${webhook}")
