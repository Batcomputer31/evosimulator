# EQ Evidence Activation Layer (21-token system)
# Author: RA (Batcomputer31)
# Purpose: Authenticate email-based EQ actions via SHA-1 tokens

AUTHORIZED_EMAILS = {
    "EVO-Lution31@proton.me": "Evo-lution",
    "batcomputer31@example.com": "Evo-locker"
}

VALID_HASHES = {
    "8bcd3e2b71bfb56f570f2a9a40fc35aac537baa7",
    "d093765c85774563f6d3ca309505347721733e16",
    "579debb25550e40d0d881d619410e70f2a5acaa9",
    "46764fb9a40ef14b5d5b6a1ae72c090b153bc453",
    "e78e99483799cb6c0b7294518ebd8de0b25e7594",
    "88ccd5e7d51a807b1487a668fda836a714fd26c9",
    "abd2a6f12bb7aea337f0525cf376e5c762922a71",
    "fb17aebab8f5e2d0849d6ebdc925d361c5d868f1",

    "2393363e975f6e42bb1e4b2accc10655fc1a8799",
    "377f5da421b21023cd897eb0124075555bb6d3d1",
    "a724389ebd96039efcbf360c0c70d40e88f08fe2",
    "e8a8caaaa97da057d03129ae7dce946ee5b33b5c",
    "b39c223656df60a74ae9ba36063d946a1705bdd0",
    "19886ea715e6f58e76d9e92567f098f3663b9147",
    "74a78b1af9f56e3ce9bb425e46a3eab4babb756c",
    "1e63b0109c57e0bef00b7bcc28266d811dd9a05d",
    "a94c56b7c70e76d550cb555ee2dde33a6c66fd64",
    "d41003d785d0c77aca6fd387cd8df11c50e46254",
    "393518071e8b355d4306d520ba723164efcc6284",
    "d3dfb42903eb2d68ad3c0b959d0f2fc41e58f6a1",
    "5681eeccda44c73b71606af9e0c63da2802c18b8"
}

def activate_email(evidence_email, message_body):
    if evidence_email not in AUTHORIZED_EMAILS:
        print("🚫 Email not recognized.")
        return False

    if not any(valid_hash in message_body for valid_hash in VALID_HASHES):
        print("🚫 No valid activation hash found in message.")
        return False

    node = AUTHORIZED_EMAILS[evidence_email]
    print(f"✅ Evidence accepted. Node '{node}' activated from {evidence_email}")
    return True

# Example Test Run
if __name__ == "__main__":
    email = "EVO-Lution31@proton.me"
    body = "Triggering node with hash: d41003d785d0c77aca6fd387cd8df11c50e46254"
    activate_email(email, body)
